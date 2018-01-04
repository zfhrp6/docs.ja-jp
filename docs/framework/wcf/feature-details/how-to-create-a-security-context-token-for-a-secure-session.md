---
title: "方法 : セキュリティで保護されたセッションに対しセキュリティ コンテキスト トークンを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
caps.latest.revision: "14"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3dc0e44e7f561e39128e32d3af5fbd495316fdd3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="639f3-102">方法 : セキュリティで保護されたセッションに対しセキュリティ コンテキスト トークンを作成する</span><span class="sxs-lookup"><span data-stu-id="639f3-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="639f3-103">セキュリティで保護されたセッションでステートフルなセキュリティ コンテキスト トークン (SCT: Security Context Token) を使用すると、そのセッションでサービスを再利用できます。</span><span class="sxs-lookup"><span data-stu-id="639f3-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="639f3-104">たとえば、セキュリティで保護されたセッションでステートレスな SCT を使用しているときにインターネット インフォメーション サービス (IIS) をリセットすると、サービスに関連付けられているセッション データが失われます。</span><span class="sxs-lookup"><span data-stu-id="639f3-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="639f3-105">このセッション データには、SCT キャッシュが含まれています。</span><span class="sxs-lookup"><span data-stu-id="639f3-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="639f3-106">このため、クライアントが次回ステートレスな SCT をサービスに送信すると、エラーが返されます。これは、SCT に関連付けられているキーを取得できないためです。</span><span class="sxs-lookup"><span data-stu-id="639f3-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="639f3-107">しかし、ステートフルな SCT を使用した場合、SCT に関連付けられているキーは、その SCT 内に格納されます。</span><span class="sxs-lookup"><span data-stu-id="639f3-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="639f3-108">キーが SCT 内、つまりメッセージ内に格納されているため、セキュリティで保護されたセッションは、サービスの再使用の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="639f3-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="639f3-109">既定では、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] は、セキュリティで保護されたセッションでステートレスな SCT を使用します。</span><span class="sxs-lookup"><span data-stu-id="639f3-109">By default, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="639f3-110">ここでは、セキュリティで保護されたセッションでステートフルな SCT を使用する方法について詳しく説明します。</span><span class="sxs-lookup"><span data-stu-id="639f3-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="639f3-111"><xref:System.ServiceModel.Channels.IDuplexChannel> から派生したコントラクトに関係する、セキュリティで保護されたセッションでは、ステートフルな SCT を使用できません。</span><span class="sxs-lookup"><span data-stu-id="639f3-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="639f3-112">セキュリティで保護されたセッションでステートフルな SCT を使用するアプリケーションでは、サービスのスレッド ID は、関連付けられたユーザー プロファイルを持つユーザー アカウントである必要があります。</span><span class="sxs-lookup"><span data-stu-id="639f3-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="639f3-113">ユーザー プロファイルを持たないアカウント (`Local Service` など) でサービスを実行すると、例外がスローされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="639f3-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="639f3-114">Windows XP で偽装が必要な場合は、ステートフルな SCT を使用しない、セキュリティで保護されたセッションを使用します。</span><span class="sxs-lookup"><span data-stu-id="639f3-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="639f3-115">ステートフル SCT が偽装と共に使用されると、<xref:System.InvalidOperationException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="639f3-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="639f3-116">[サポートされていないシナリオ](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)です。</span><span class="sxs-lookup"><span data-stu-id="639f3-116"> [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="639f3-117">セキュリティで保護されたセッションでステートフルな SCT を使用するには</span><span class="sxs-lookup"><span data-stu-id="639f3-117">To use stateful SCTs in a secure session</span></span>  
  
-   <span data-ttu-id="639f3-118">ステートフルな SCT を使用する、セキュリティで保護されたセッションによって SOAP メッセージを保護するように指定するカスタム バインドを作成します。</span><span class="sxs-lookup"><span data-stu-id="639f3-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1.  <span data-ttu-id="639f3-119">追加することで、カスタム バインドを定義、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)サービスの構成ファイルにします。</span><span class="sxs-lookup"><span data-stu-id="639f3-119">Define a custom binding, by adding a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  <span data-ttu-id="639f3-120">追加、 [\<バインディング >](../../../../docs/framework/misc/binding.md)に子要素、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="639f3-120">Add a [\<binding>](../../../../docs/framework/misc/binding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="639f3-121">`name` 属性を、構成ファイル内で一意の名前に設定してバンディング名を指定します。</span><span class="sxs-lookup"><span data-stu-id="639f3-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  <span data-ttu-id="639f3-122">このサービスとの間を追加することによって送信されるメッセージの認証モードを指定、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)に子要素、 [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="639f3-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="639f3-123">`authenticationMode` 属性を `SecureConversation` に設定して、セキュリティで保護されたセッションを指定します。</span><span class="sxs-lookup"><span data-stu-id="639f3-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="639f3-124">`requireSecurityContextCancellation` 属性を `false` に設定して、ステートフルな SCT を使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="639f3-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  <span data-ttu-id="639f3-125">追加することにより、セキュリティで保護されたセッションを確立中にクライアントを認証する方法を指定、 [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)に子要素、 [\<セキュリティ >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="639f3-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="639f3-126">クライアントの認証方法は、`authenticationMode` 属性を設定して指定します。</span><span class="sxs-lookup"><span data-stu-id="639f3-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  <span data-ttu-id="639f3-127">など、エンコード要素を追加することによって、メッセージ エンコーディングを指定する[ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)です。</span><span class="sxs-lookup"><span data-stu-id="639f3-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  <span data-ttu-id="639f3-128">などのトランスポート要素を追加することによって、トランスポートを指定、 [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)です。</span><span class="sxs-lookup"><span data-stu-id="639f3-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="639f3-129">次のコード例では、構成を使用して、セキュリティで保護されたセッションでメッセージがステートフルな SCT と共に使用できるカスタム バインドを指定します。</span><span class="sxs-lookup"><span data-stu-id="639f3-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="StatefulSCTSecureSession">  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
          <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        </security>  
        <textMessageEncoding />  
        <httpTransport />  
      </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="639f3-130">例</span><span class="sxs-lookup"><span data-stu-id="639f3-130">Example</span></span>  
 <span data-ttu-id="639f3-131">セキュリティで保護されたセッションをブートストラップするための <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> 認証モードを使用する、カスタム バインディングを作成するコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="639f3-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="639f3-132">Windows 認証をステートフルな SCT と組み合わせて使用すると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> プロパティに実際の呼び出し元の ID が設定されず、代わりに "anonymous" が設定されます。</span><span class="sxs-lookup"><span data-stu-id="639f3-132">When Windows authentication is used in combination with a stateful SCT, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="639f3-133">その場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のセキュリティは、受信 SCT からの要求ごとにサービスのセキュリティ コンテキストの内容を再作成する必要があるため、サーバーはメモリ内でセキュリティ セッションを追跡できません。</span><span class="sxs-lookup"><span data-stu-id="639f3-133">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="639f3-134">また、<xref:System.Security.Principal.WindowsIdentity> インスタンスは SCT にシリアル化できないため、<xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> プロパティは匿名 ID を返します。</span><span class="sxs-lookup"><span data-stu-id="639f3-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="639f3-135">次の構成は、この動作を示します。</span><span class="sxs-lookup"><span data-stu-id="639f3-135">The following configuration exhibits this behavior.</span></span>  
  
```xml  
<customBinding>  
  <binding name="Cancellation">  
       <textMessageEncoding />  
        <security   
            requireSecurityContextCancellation="false">  
              <secureConversationBootstrap />  
      </security>  
    <httpTransport />  
  </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="639f3-136">参照</span><span class="sxs-lookup"><span data-stu-id="639f3-136">See Also</span></span>  
 [<span data-ttu-id="639f3-137">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="639f3-137">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
