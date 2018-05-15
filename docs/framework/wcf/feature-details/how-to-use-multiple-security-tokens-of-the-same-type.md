---
title: '方法 : 同じ型の複数のセキュリティ トークンを使用する'
ms.date: 03/30/2017
ms.assetid: cf179f48-4ed4-4caa-86a5-ef8eecc231cd
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 67a9fd51377294ab6afb5a3d7deaec19fb134b21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="7c064-102">方法 : 同じ型の複数のセキュリティ トークンを使用する</span><span class="sxs-lookup"><span data-stu-id="7c064-102">How to: Use Multiple Security Tokens of the Same Type</span></span>
-   <span data-ttu-id="7c064-103">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0 では、クライアント メッセージには任意の型のトークンを 1 つしか含めることができませんでしたが、</span><span class="sxs-lookup"><span data-stu-id="7c064-103">In [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 3.0, a client message only contained one token of any given type.</span></span> <span data-ttu-id="7c064-104">現在は、同じ型の複数のトークンをクライアント メッセージに含めることができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="7c064-104">Now client messages can contain multiple tokens of a type.</span></span> <span data-ttu-id="7c064-105">このトピックでは、同じ型の複数のトークンをクライアント メッセージに含める方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="7c064-105">This topic shows how to include multiple tokens of the same type in a client message.</span></span>  
  
-   <span data-ttu-id="7c064-106">この方法でサービスを構成することはできません。サービスに含めることができるサポート トークンは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="7c064-106">Note that you cannot configure a service in this way: a service can contain only one supporting token.</span></span>  
  
### <a name="to-use-multiple-security-tokens-of-the-same-type"></a><span data-ttu-id="7c064-107">同じ型の複数のセキュリティ トークンを使用するには</span><span class="sxs-lookup"><span data-stu-id="7c064-107">To use multiple security tokens of the same type</span></span>  
  
1.  <span data-ttu-id="7c064-108">設定する空のバインド要素コレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="7c064-108">Create an empty binding element collection to be populated.</span></span>  
  
     [!code-csharp[C_CustomBinding#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#9)]  
  
2.  <span data-ttu-id="7c064-109"><xref:System.ServiceModel.Channels.SecurityBindingElement> を呼び出して <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> を作成します。</span><span class="sxs-lookup"><span data-stu-id="7c064-109">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> by calling <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>.</span></span>  
  
     [!code-csharp[C_CustomBinding#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#10)]  
  
3.  <span data-ttu-id="7c064-110"><xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> のコレクションを作成します。</span><span class="sxs-lookup"><span data-stu-id="7c064-110">Create a <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters> collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#11)]  
  
4.  <span data-ttu-id="7c064-111">SAML トークンをコレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="7c064-111">Add SAML tokens to the collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#12)]  
  
5.  <span data-ttu-id="7c064-112">コレクションを <xref:System.ServiceModel.Channels.SecurityBindingElement> に追加します。</span><span class="sxs-lookup"><span data-stu-id="7c064-112">Add the collection to the <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span></span>  
  
     [!code-csharp[C_CustomBinding#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#13)]  
  
6.  <span data-ttu-id="7c064-113">バインド要素をバインド要素コレクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="7c064-113">Add binding elements to the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#14)]  
  
7.  <span data-ttu-id="7c064-114">作成した新しいカスタム バインディングをバインド要素コレクションから返します。</span><span class="sxs-lookup"><span data-stu-id="7c064-114">Return a new custom binding created from the binding element collection.</span></span>  
  
     [!code-csharp[C_CustomBinding#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#15)]  
  
## <a name="example"></a><span data-ttu-id="7c064-115">例</span><span class="sxs-lookup"><span data-stu-id="7c064-115">Example</span></span>  
 <span data-ttu-id="7c064-116">上記の手順で説明したメソッド全体を次に示します。</span><span class="sxs-lookup"><span data-stu-id="7c064-116">The following is the entire method described by the preceding procedure.</span></span>  
  
 [!code-csharp[C_CustomBinding#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombinding/cs/c_custombinding.cs#7)]  
  
## <a name="see-also"></a><span data-ttu-id="7c064-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c064-117">See Also</span></span>  
 [<span data-ttu-id="7c064-118">セキュリティ アーキテクチャ</span><span class="sxs-lookup"><span data-stu-id="7c064-118">Security Architecture</span></span>](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
