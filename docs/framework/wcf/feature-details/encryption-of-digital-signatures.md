---
title: "電子署名の暗号化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption of digital signatures [WCF]
- digital signatures [WCF], encryption
- digital signatures [WCF]
ms.assetid: 0868866d-40b4-4341-8e42-eee3b7f15b69
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 147f62a895983557267d0a18fdd1ea261ae6c855
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="encryption-of-digital-signatures"></a><span data-ttu-id="40229-102">電子署名の暗号化</span><span class="sxs-lookup"><span data-stu-id="40229-102">Encryption of Digital Signatures</span></span>
<span data-ttu-id="40229-103">既定では、メッセージは署名および暗号化され、署名はデジタル暗号化されます。</span><span class="sxs-lookup"><span data-stu-id="40229-103">By default, a message is signed and encrypted, and the signature is digitally encrypted.</span></span> <span data-ttu-id="40229-104">これは、<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> または <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> のインスタンスを使用してカスタム バインディングを作成し、いずれかのクラスの `MessageProtectionOrder` プロパティを <xref:System.ServiceModel.Security.MessageProtectionOrder> 列挙値に設定することによって制御できます。</span><span class="sxs-lookup"><span data-stu-id="40229-104">You can control this by creating a custom binding with an instance of the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> or the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and then setting the `MessageProtectionOrder` property of either class to a <xref:System.ServiceModel.Security.MessageProtectionOrder> enumeration value.</span></span> <span data-ttu-id="40229-105">既定値は、<xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature> です。</span><span class="sxs-lookup"><span data-stu-id="40229-105">The default is <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncryptAndEncryptSignature>.</span></span> <span data-ttu-id="40229-106">このプロセスは、単に署名して暗号化する場合よりも時間が 10 ～ 40 % 長くかかります。</span><span class="sxs-lookup"><span data-stu-id="40229-106">This process takes 10 to 40 percent longer than simply signing and encrypting.</span></span> <span data-ttu-id="40229-107">ただし、署名の暗号化を無効にすると、攻撃者がメッセージの内容を予想できるようになる恐れがあります。</span><span class="sxs-lookup"><span data-stu-id="40229-107">Disabling encryption of the signature, however, might allow an attacker to guess the contents of the message.</span></span> <span data-ttu-id="40229-108">その理由は、メッセージ内のすべての署名部分のプレーン テキストのハッシュ コードが署名要素に含まれるからです。</span><span class="sxs-lookup"><span data-stu-id="40229-108">This is possible because the signature element contains the hash code of the plain text of every signed part in the message.</span></span> <span data-ttu-id="40229-109">たとえば、メッセージ本体は既定で暗号化されますが、暗号化されていない署名には、メッセージ本体のハッシュ コードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="40229-109">For example, although the message body is encrypted by default, the unencrypted signature contains the hash code of the message body.</span></span> <span data-ttu-id="40229-110">メッセージが短い場合は、攻撃者に内容を推測されてしまうおそれがあります。</span><span class="sxs-lookup"><span data-stu-id="40229-110">If the message is small, an attacker might be able to deduce the contents.</span></span> <span data-ttu-id="40229-111">署名を暗号化すると、このような危険性が低減または解消されます。</span><span class="sxs-lookup"><span data-stu-id="40229-111">Encrypting the signature reduces or eliminates this possibility.</span></span>  
  
 <span data-ttu-id="40229-112">そのため、署名の暗号化を無効にするのは、セキュリティに影響しない大型のバイナリ ファイルを送信する場合などの、内容の重要性が低く、パフォーマンスの向上が重要な場合に限定してください。</span><span class="sxs-lookup"><span data-stu-id="40229-112">Therefore, disable encryption of the signature only when the value of the content is low, and the performance gain will be significant, for example, when sending large binary files that have no security implications.</span></span>  
  
### <a name="to-disable-digital-signing"></a><span data-ttu-id="40229-113">デジタル署名を無効にするには</span><span class="sxs-lookup"><span data-stu-id="40229-113">To disable digital signing</span></span>  
  
1.  <span data-ttu-id="40229-114"><xref:System.ServiceModel.Channels.CustomBinding> を作成します。</span><span class="sxs-lookup"><span data-stu-id="40229-114">Create a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="40229-115">[する方法: SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)です。</span><span class="sxs-lookup"><span data-stu-id="40229-115"> [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
2.  <span data-ttu-id="40229-116"><xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> または <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> をバインディング コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="40229-116">Add either an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> or a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> to the binding collection.</span></span>  
  
3.  <span data-ttu-id="40229-117"><xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> プロパティを <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> に設定するか、または <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> プロパティを <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt> に設定します。</span><span class="sxs-lookup"><span data-stu-id="40229-117">Set the <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> property to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>, or set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.MessageProtectionOrder%2A?displayProperty=nameWithType> property to <xref:System.ServiceModel.Security.MessageProtectionOrder.SignBeforeEncrypt>.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="40229-118">カスタム バインディングを作成するを参照してください[ユーザー定義バインディング](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)です。</span><span class="sxs-lookup"><span data-stu-id="40229-118"> creating custom bindings, see [Creating User-Defined Bindings](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="40229-119">特定の認証モード用のカスタム バインドを作成するを参照してください[する方法: 指定された認証モードでは、SecurityBindingElement を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)です。</span><span class="sxs-lookup"><span data-stu-id="40229-119"> creating a custom binding for a specific authentication mode, see [How to: Create a SecurityBindingElement for a Specified Authentication Mode](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40229-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="40229-120">See Also</span></span>  
 <xref:System.ServiceModel.Security.MessageProtectionOrder>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 [<span data-ttu-id="40229-121">方法: SecurityBindingElement を使用してカスタム バインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="40229-121">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="40229-122">ユーザー定義のバインディングを作成します。</span><span class="sxs-lookup"><span data-stu-id="40229-122">Creating User-Defined Bindings</span></span>](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)  
 [<span data-ttu-id="40229-123">方法: 指定された認証モード用の SecurityBindingElement を作成</span><span class="sxs-lookup"><span data-stu-id="40229-123">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
