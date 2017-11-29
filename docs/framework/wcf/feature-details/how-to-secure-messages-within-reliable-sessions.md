---
title: "方法 : 信頼できるセッション内でメッセージをセキュリティで保護する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3f27b1a4de2019660e0facb081300a79eae65b99
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="7d940-102">方法 : 信頼できるセッション内でメッセージをセキュリティで保護する</span><span class="sxs-lookup"><span data-stu-id="7d940-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="7d940-103">ここでは、信頼できるセッション内で交換されるメッセージに対して、メッセージ レベルのセキュリティを有効にするために必要な手順について説明します。このとき、信頼できるセッションがオプションでサポートされているシステム指定のバインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="7d940-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="7d940-104">コードを使用して強制的に行うか、宣言、構成ファイルでは、セキュリティで保護された信頼できるセッションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="7d940-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="7d940-105">この手順では、クライアントとサービスの構成ファイルを使用して、セキュリティで保護された信頼できるセッションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="7d940-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="7d940-106">この手順の主な部分は、次の 3 つの作業で構成されます。</span><span class="sxs-lookup"><span data-stu-id="7d940-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="7d940-107">クライアントとサービスのメッセージ交換は信頼できるセッション内で行うことを指定します。</span><span class="sxs-lookup"><span data-stu-id="7d940-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="7d940-108">信頼できるセッション内でメッセージ レベルのセキュリティを要求します。</span><span class="sxs-lookup"><span data-stu-id="7d940-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="7d940-109">サービスに対する認証時にクライアントが使用する必要があるクライアント資格情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="7d940-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="7d940-110">エンドポイント構成要素を含む最初のタスクで重要な`bindingConfiguration`に (この例の) という名前のバインディング構成を参照する属性を`MessageSecurity`です。</span><span class="sxs-lookup"><span data-stu-id="7d940-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="7d940-111">[ **\<バインディング >** ](../../../../docs/framework/misc/binding.md)構成要素を設定して、信頼できるセッションを有効にするには、この名前を参照し、`enabled`の属性、 [  **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)要素を`true`です。</span><span class="sxs-lookup"><span data-stu-id="7d940-111">The [**\<binding>**](../../../../docs/framework/misc/binding.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element to `true`.</span></span> <span data-ttu-id="7d940-112">信頼できるセッション内で使用できる順序付き配信の保証は、`ordered` 属性を `true` に設定することによって要求できます。</span><span class="sxs-lookup"><span data-stu-id="7d940-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="7d940-113">この構成手順を基になる例の元のコピーを次を参照してください。、 [WS 信頼できるセッション](../../../../docs/framework/wcf/samples/ws-reliable-session.md)です。</span><span class="sxs-lookup"><span data-stu-id="7d940-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="7d940-114">設定して行われます 2 番目のタスクの重要な項目、`mode`の属性、 **\<セキュリティ >**要素に含まれている、 **\<バインディング >** 。要素のクライアントとサービスを`Message`です。</span><span class="sxs-lookup"><span data-stu-id="7d940-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="7d940-115">設定して行われます 3 番目のタスクの重要な項目、`clientCredentialType`の属性、 **\<メッセージ >**要素に含まれている、 **\<セキュリティ >** 。要素のクライアントとサービスを`Certificate`です。</span><span class="sxs-lookup"><span data-stu-id="7d940-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="7d940-116">メッセージ セキュリティを使用して、信頼できるセッションで、最初のエラー発生時に例外をスローする代わりに、タイムアウトが発生するまでは、認証されていないクライアントを認証すると信頼性の高いメッセージングされます。</span><span class="sxs-lookup"><span data-stu-id="7d940-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="7d940-117">信頼できるセッションを使用する WSHttpBinding でサービスを構成します。</span><span class="sxs-lookup"><span data-stu-id="7d940-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="7d940-118">この手順で説明されて[する方法: Exchange メッセージ内で、信頼できるセッション](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)です。</span><span class="sxs-lookup"><span data-stu-id="7d940-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="7d940-119">信頼できるセッションを使用する WSHttpBinding でクライアントを構成します。</span><span class="sxs-lookup"><span data-stu-id="7d940-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="7d940-120">この手順で説明されて[する方法: Exchange メッセージ内で、信頼できるセッション](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)です。</span><span class="sxs-lookup"><span data-stu-id="7d940-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="7d940-121">構成でモードと ClientCredentialType を設定します。</span><span class="sxs-lookup"><span data-stu-id="7d940-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="7d940-122">適切なバインド要素を追加、 [ **\<バインド >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)構成ファイルの要素。</span><span class="sxs-lookup"><span data-stu-id="7d940-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="7d940-123">次の例では追加、 [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)要素。</span><span class="sxs-lookup"><span data-stu-id="7d940-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="7d940-124">追加、 **\<バインディング >**要素とその`name`属性を適切な値にします。</span><span class="sxs-lookup"><span data-stu-id="7d940-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="7d940-125">例では、名前を使用して`MessageSecurity`です。</span><span class="sxs-lookup"><span data-stu-id="7d940-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="7d940-126">追加、 **\<セキュリティ >**要素、`mode`属性を`Message`です。</span><span class="sxs-lookup"><span data-stu-id="7d940-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="7d940-127">内で、 **\<セキュリティ >**要素を追加、 **\<メッセージ >**要素、`clientCredentialType`属性を`Certificate`です。</span><span class="sxs-lookup"><span data-stu-id="7d940-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
