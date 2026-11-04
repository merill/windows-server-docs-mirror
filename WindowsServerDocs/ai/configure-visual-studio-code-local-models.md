---
layout: Conceptual
title: Visual Studio Code Custom Model Endpoints | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/windows-server/ai/configure-visual-studio-code-local-models
breadcrumb_path: /windows-server/breadcrumbs/toc.json
uhfHeaderId: MSDocsHeader-WindowsServer
feedback_system: Standard
recommendations: true
ms.update-cycle: 1095-days
description: Learn how to connect Visual Studio Code to an OpenAI-compatible model endpoint on the same device or hosted remotely on Windows Server.
ms.topic: install-set-up-deploy
author: robinharwood
ms.author: roharwoo
ms.service: windows-server
ms.date: 2026-09-25T00:00:00.0000000Z
ai-usage: ai-assisted
locale: en-us
document_id: 392e69b2-e3f4-419f-60f4-c84e282d85ee
document_version_independent_id: 392e69b2-e3f4-419f-60f4-c84e282d85ee
original_content_git_url: https://github.com/MicrosoftDocs/windowsserverdocs-pr/blob/live/WindowsServerDocs/ai/configure-visual-studio-code-local-models.md
site_name: Docs
depot_name: MSDN.WindowsServerDocs-pr
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.WindowsServerDocs-pr/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: ai/configure-visual-studio-code-local-models
moniker_range_name: 
monikers: []
item_type: Content
source_path: WindowsServerDocs/ai/configure-visual-studio-code-local-models.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/911a44a7-2f6c-477c-810f-dc8b7d425cce
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/14f2b9d5-6f06-45a8-ac5f-313eaa351153
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: 23a7c818-5ec5-40cd-2fc1-8ff3479350d1
---

# Visual Studio Code Custom Model Endpoints | Microsoft Learn

Visual Studio Code can connect the **Chat** view to an OpenAI-compatible inference endpoint for a locally hosted model. The endpoint can run on the same Windows 11 device as Visual Studio Code or on Windows Server for access from one or more remote Windows 11 clients. These topologies let you keep inference on a developer device or centralize model compute without running Visual Studio Code on Windows Server.

In this article, you add an existing endpoint as a custom endpoint in Visual Studio Code, select its model, and verify that the model responds. The procedure assumes that the inference endpoint is already running and reachable from Visual Studio Code.

## Prerequisites for local and remote model endpoints

- [Download the current stable release of Visual Studio Code](https://code.visualstudio.com/download), and ensure that you can access the **Chat** view.
- An existing OpenAI-compatible endpoint that supports the Chat Completions API and is reachable from the computer running Visual Studio Code.
- For a remote endpoint hosted on Windows Server, network connectivity from the Windows 11 client to the server and endpoint port. Configure Windows Firewall and any intervening firewall or proxy to permit the connection. Configure the endpoint to listen on a network interface that remote clients can reach, not only on a loopback address.
- For a remote endpoint that uses a host name, a Domain Name System (DNS) record that the Windows 11 client can resolve to the Windows Server host.
- For a remote HTTPS endpoint, a valid TLS certificate that the Windows 11 client trusts and whose subject name or subject alternative name matches the host name in the endpoint URL.
- Endpoint access controls that permit the Windows 11 client to call the Chat Completions route. Obtain any required API key or token from the endpoint administrator.
- For same-device inference, the loopback URL that the endpoint exposes, such as `http://localhost:<port>/v1/chat/completions`.
- For remote inference, a trusted HTTPS URL, such as `https://<server-name>:<port>/v1/chat/completions`.
- The exact model ID; a model display name, which Visual Studio Code shows in the **language model picker**; context limits; and supported capabilities from the endpoint owner or model documentation.
- The authentication header requirements for the endpoint.
- If your organization manages GitHub Copilot, it must enable the **Bring Your Own Language Model Key in VS Code** policy. For more information, see [Bring your own language model key in VS Code](https://code.visualstudio.com/docs/agent-customization/language-models#_bring-your-own-language-model-key).

You don't need a GitHub account or a GitHub Copilot plan to use a bring-your-own-key model in chat. The custom endpoint doesn't provide features that depend on the GitHub Copilot service, including inline suggestions, semantic search, and embeddings.

## Add a custom local or remote model endpoint

The same procedure supports an endpoint on the same Windows 11 device or a remote OpenAI-compatible endpoint on Windows Server. Visual Studio Code connects to one endpoint URL, and the endpoint service manages backend inference distribution.

1. In Visual Studio Code, open the **Chat** view.
2. Open the **language model picker**, and then select **Manage Language Models** (**gear icon**).

    You can also open the **Command Palette** and run **Chat: Manage Language Models**.
3. In the **Language Models** editor, select **Add Models**, and then select **Custom Endpoint**.
4. Enter a group name. This name identifies the endpoint's models in the **language model picker** and the **Language Models** editor.
5. Enter the model display name and the API key for the endpoint.
6. For the API type, select **Chat Completions**.
7. In the `chatLanguageModels.json` file that Visual Studio Code opens, configure the model properties, and then save the file.

    Use the endpoint and model documentation to set the properties. At minimum, confirm the following values:

    | Property | Value |
    | --- | --- |
    | `id` | The exact model ID that the endpoint expects. |
    | `name` | The model display name that Visual Studio Code shows in the **language model picker**. |
    | `url` | The full route, such as `https://<server-name>:<port>/v1/chat/completions`. |
    | `apiType` | `chat-completions` |
    | `toolCalling` | `true` only if the endpoint and model support tool calling. |
    | `vision` | `true` only if the endpoint and model support image input. |
    | `maxInputTokens` | The model's supported maximum input token count. |
    | `maxOutputTokens` | The model's supported maximum output token count. |

    Keep the generated `apiKey` input reference instead of placing the API key directly in `chatLanguageModels.json`. Visual Studio Code sends the key in an `Authorization: Bearer <api-key>` header by default for Chat Completions custom endpoints.

    If the endpoint requires a different authentication header, configure the model's `requestHeaders` property and use the `${apiKey}` token as the header value. Don't place a raw secret in the configuration file. For the supported properties and authentication behavior, see [Custom Endpoint configuration reference](https://code.visualstudio.com/docs/agent-customization/language-models#_custom-endpoint-configuration-reference).

## Select and verify a local or remote endpoint model

1. Return to the **Chat** view and open the **language model picker**.
2. Select the model under the group name that you configured.
3. Enter a short test prompt, such as:

    ```text
    Reply with one sentence that confirms you received this request.
    ```
4. Confirm that the **Chat** view displays a response from the selected model.
5. If you have access to the inference endpoint logs, confirm that the endpoint received the request for the configured model ID.

The configuration is working when the selected model returns a response and the endpoint records the request.

Note

A model must support tool calling to be available for agents in chat. Don't set `toolCalling` to `true` unless the endpoint and model support that capability.

## Troubleshoot local and remote model endpoints in Visual Studio Code

| Issue | What to check |
| --- | --- |
| **Custom Endpoint** isn't available | Update to the current stable release of Visual Studio Code. If your organization manages GitHub Copilot, confirm that your organization enables the bring-your-own-key policy. |
| The model doesn't appear in the model picker | Save `chatLanguageModels.json`, and then restart Visual Studio Code. In a workspace in **Restricted Mode**, trust the workspace to restore the full model list. For agent use, also confirm that the model supports tool calling and that `toolCalling` is `true`. |
| The endpoint returns an authentication error | Confirm that the API key is current and that its authentication header matches the endpoint requirements. If the endpoint requires another header, configure `requestHeaders` with the `${apiKey}` token. |
| The endpoint returns a route or API error | Confirm that `apiType` is `chat-completions` and that `url` contains the full Chat Completions route, including `/v1/chat/completions` when the endpoint exposes that route. |
| A remote client can't connect to the endpoint | Confirm that the Windows 11 client can resolve the server host name and reach the endpoint port. Check the endpoint listener address, Windows Firewall, and any intervening firewall or proxy. |
| A remote endpoint returns a TLS or certificate error | Confirm that the certificate is valid, that the Windows 11 client trusts it, and that it covers the host name in the endpoint URL. |
| The endpoint denies a remote client | Confirm that the endpoint access controls permit the client to call the Chat Completions route and that the configured credential has access to the requested model. |
| The request reaches the endpoint but inference fails | Confirm that the model ID exactly matches the endpoint's model ID and that the endpoint supports the requested model capabilities. Review the endpoint logs for the request failure. |