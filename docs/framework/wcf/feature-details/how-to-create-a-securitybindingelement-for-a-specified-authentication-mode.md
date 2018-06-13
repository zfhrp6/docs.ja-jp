---
title: '方法 : 指定した認証モード用の SecurityBindingElement を作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 70c3e371be3af5f03ea85f1681155c2590d42373
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33489532"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a><span data-ttu-id="5d2ea-102">方法 : 指定した認証モード用の SecurityBindingElement を作成する</span><span class="sxs-lookup"><span data-stu-id="5d2ea-102">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>
<span data-ttu-id="5d2ea-103">Windows Communication Foundation (WCF) では、クライアントとサービスを相互に認証するいくつかのモードを提供します。</span><span class="sxs-lookup"><span data-stu-id="5d2ea-103">Windows Communication Foundation (WCF) provides several modes by which clients and services authenticate to one another.</span></span> <span data-ttu-id="5d2ea-104">これらの認証モード用のセキュリティ バインド要素は、次の例のように、<xref:System.ServiceModel.Channels.SecurityBindingElement> クラスの静的メソッドまたは構成を使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="5d2ea-104">You can create security binding elements for these authentication modes by using static methods on the <xref:System.ServiceModel.Channels.SecurityBindingElement> class or through configuration, as shown in the following example.</span></span>  
  
 <span data-ttu-id="5d2ea-105">18 の認証モードの詳細については、次を参照してください。 [SecurityBindingElement 認証モード](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)です。</span><span class="sxs-lookup"><span data-stu-id="5d2ea-105">For more information about the 18 authentication modes, see [SecurityBindingElement Authentication Modes](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d2ea-106">例</span><span class="sxs-lookup"><span data-stu-id="5d2ea-106">Example</span></span>  
 <span data-ttu-id="5d2ea-107">次のコード例では、複数の認証モードのバインディングを作成するメソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="5d2ea-107">The following code example shows methods for creating bindings for the various authentication modes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d2ea-108"><xref:System.ServiceModel.Channels.SecurityBindingElement> オブジェクトのインスタンスが一度作成されると、<xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> や <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A> などの多数のプロパティは変更できなくなります。</span><span class="sxs-lookup"><span data-stu-id="5d2ea-108">Once an instance of the <xref:System.ServiceModel.Channels.SecurityBindingElement> object is created, a number of properties are immutable, such as <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> and <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>.</span></span> <span data-ttu-id="5d2ea-109">これらのプロパティで `set` を呼び出しても変更されません。</span><span class="sxs-lookup"><span data-stu-id="5d2ea-109">Calling `set` on such properties does not change them.</span></span>  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5d2ea-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d2ea-110">See Also</span></span>  
 [<span data-ttu-id="5d2ea-111">SecurityBindingElement 認証モード</span><span class="sxs-lookup"><span data-stu-id="5d2ea-111">SecurityBindingElement Authentication Modes</span></span>](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [<span data-ttu-id="5d2ea-112">方法 : SecurityBindingElement を使用してカスタム バインディングを作成する</span><span class="sxs-lookup"><span data-stu-id="5d2ea-112">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
