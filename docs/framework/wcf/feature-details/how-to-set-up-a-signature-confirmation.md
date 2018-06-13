---
title: '方法 : 署名確認を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: d7076917e48124b2501826ecb0ac7599c663ba7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491990"
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="ad687-102">方法 : 署名確認を設定する</span><span class="sxs-lookup"><span data-stu-id="ad687-102">How to: Set Up a Signature Confirmation</span></span>
<span data-ttu-id="ad687-103">*署名確認*は、メッセージのイニシエーター応答を受信しましたが、送信者の元のメッセージへの応答で生成されたことを確認するためのメカニズムです。</span><span class="sxs-lookup"><span data-stu-id="ad687-103">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="ad687-104">署名確認は、WS-Security 1.1 仕様で定義されています。</span><span class="sxs-lookup"><span data-stu-id="ad687-104">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="ad687-105">エンドポイントが WS-Security 1.0 をサポートしている場合は、署名確認を使用できません。</span><span class="sxs-lookup"><span data-stu-id="ad687-105">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>  
  
 <span data-ttu-id="ad687-106">以下の手順では、<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> を使用して署名確認を有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ad687-106">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="ad687-107"><xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> でも同じ手順を使用できます。</span><span class="sxs-lookup"><span data-stu-id="ad687-107">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="ad687-108">基本的な手順については、基にして、プロシージャ構築[する方法: SecurityBindingElement 作成するカスタム バインドを使用して、](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad687-108">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="ad687-109">コードを使用して署名確認を有効にするには</span><span class="sxs-lookup"><span data-stu-id="ad687-109">To enable signature confirmation in code</span></span>  
  
1.  <span data-ttu-id="ad687-110"><xref:System.ServiceModel.Channels.BindingElementCollection> クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="ad687-110">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>  
  
2.  <span data-ttu-id="ad687-111">インスタンスを作成、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>クラスです。</span><span class="sxs-lookup"><span data-stu-id="ad687-111">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>  
  
3.  <span data-ttu-id="ad687-112"><xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad687-112">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>  
  
4.  <span data-ttu-id="ad687-113">バインディング コレクションにセキュリティ要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="ad687-113">Add the security element to the binding collection.</span></span>  
  
5.  <span data-ttu-id="ad687-114">指定されている、カスタム バインディングを作成する[する方法: SecurityBindingElement を使用してカスタム バインディングを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)です。</span><span class="sxs-lookup"><span data-stu-id="ad687-114">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="ad687-115">構成を使用して署名確認を有効にするには</span><span class="sxs-lookup"><span data-stu-id="ad687-115">To enable signature confirmation in configuration</span></span>  
  
1.  <span data-ttu-id="ad687-116">`<customBinding>` 要素を構成ファイルの `<bindings>` セクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="ad687-116">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>  
  
2.  <span data-ttu-id="ad687-117">`<binding>` 要素を追加し、名前属性を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad687-117">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="ad687-118">適切なエンコード要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="ad687-118">Add an appropriate encoding element.</span></span> <span data-ttu-id="ad687-119">次の例では `<TextMessageEncoding>` 要素を追加しています。</span><span class="sxs-lookup"><span data-stu-id="ad687-119">The following example adds a `<TextMessageEncoding>` element.</span></span>  
  
4.  <span data-ttu-id="ad687-120">`<security>` 子要素を追加し、`requireSignatureConfirmation` 属性を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="ad687-120">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>  
  
5.  <span data-ttu-id="ad687-121">任意。</span><span class="sxs-lookup"><span data-stu-id="ad687-121">Optional.</span></span> <span data-ttu-id="ad687-122">ブートス トラップ中に署名確認を有効にするには追加、 [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)子要素、`equireSignatureConfirmation`属性を`true`です。</span><span class="sxs-lookup"><span data-stu-id="ad687-122">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `equireSignatureConfirmation` attribute to `true`.</span></span>  
  
6.  <span data-ttu-id="ad687-123">適切なトランスポート要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="ad687-123">Add an appropriate transport element.</span></span> <span data-ttu-id="ad687-124">次の例では追加、 [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span><span class="sxs-lookup"><span data-stu-id="ad687-124">The following example adds an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SignatureConfirmationBinding">  
          <security requireSignatureConfirmation="true">  
            <secureConversationBootstrap requireSignatureConfirmation="true" />  
              </security>  
           <textMessageEncoding />  
             <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="example"></a><span data-ttu-id="ad687-125">例</span><span class="sxs-lookup"><span data-stu-id="ad687-125">Example</span></span>  
 <span data-ttu-id="ad687-126">次のコードでは、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> のインスタンスを作成し、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> プロパティを `true` に設定しています。</span><span class="sxs-lookup"><span data-stu-id="ad687-126">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="ad687-127">この例では、前の例で示した `<secureConversationBootstrap>` 要素は使用していません。</span><span class="sxs-lookup"><span data-stu-id="ad687-127">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="ad687-128">この例は、Windows (Kerberos プロトコル) トークンを使用した場合の署名確認を示しています。</span><span class="sxs-lookup"><span data-stu-id="ad687-128">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="ad687-129">この場合、クライアントの署名はサービスからのすべての応答で返され、クライアントによって確認されます。</span><span class="sxs-lookup"><span data-stu-id="ad687-129">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="ad687-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="ad687-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>  
 [<span data-ttu-id="ad687-131">方法 : SecurityBindingElement を使用してカスタム バインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="ad687-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="ad687-132">方法 : 指定した認証モード用の SecurityBindingElement を作成する</span><span class="sxs-lookup"><span data-stu-id="ad687-132">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
