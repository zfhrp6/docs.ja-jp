---
title: "XSLT 拡張オブジェクト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 18106b74c19ffdfc33176a12bec07daf2b19b17e
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="xslt-extension-objects"></a><span data-ttu-id="d651e-102">XSLT 拡張オブジェクト</span><span class="sxs-lookup"><span data-stu-id="d651e-102">XSLT Extension Objects</span></span>
<span data-ttu-id="d651e-103">拡張オブジェクトは、スタイル シートの機能を拡張する場合に使用します。</span><span class="sxs-lookup"><span data-stu-id="d651e-103">Extension objects are used to extend the functionality of style sheets.</span></span> <span data-ttu-id="d651e-104">拡張オブジェクトは、<xref:System.Xml.Xsl.XsltArgumentList> クラスによって維持されます。</span><span class="sxs-lookup"><span data-stu-id="d651e-104">Extension objects are maintained by the <xref:System.Xml.Xsl.XsltArgumentList> class.</span></span>  
  
 <span data-ttu-id="d651e-105">埋め込みスクリプトではなく、拡張オブジェクトを使用する利点を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d651e-105">The following are advantages to using an extension object rather than embedded script:</span></span>  
  
-   <span data-ttu-id="d651e-106">クラスをより効果的にカプセル化および再利用できます。</span><span class="sxs-lookup"><span data-stu-id="d651e-106">Provides better encapsulation and reuse of classes.</span></span>  
  
-   <span data-ttu-id="d651e-107">スタイル シートを小さくすることができ、管理が簡単になります。</span><span class="sxs-lookup"><span data-stu-id="d651e-107">Allows style sheets to be smaller and more maintainable.</span></span>  
  
 <span data-ttu-id="d651e-108">XSLT 拡張オブジェクトを <xref:System.Xml.Xsl.XsltArgumentList> オブジェクトに追加するには、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="d651e-108">XSLT extension objects are added to the <xref:System.Xml.Xsl.XsltArgumentList> object using the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="d651e-109">その時点で、修飾名と名前空間 URI がその拡張オブジェクトに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="d651e-109">A qualified name and namespace URI are associated with the extension object at that time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d651e-110"><xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを呼び出すには、FullTrust アクセス許可セットが必要です。</span><span class="sxs-lookup"><span data-stu-id="d651e-110">The FullTrust permission set is required to call the <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span> <span data-ttu-id="d651e-111">詳細については、「[コード アクセス セキュリティ](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03)」と [NIB: 名前付きアクセス許可セット](http://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d651e-111">For more information, see [Code Access Security](http://msdn.microsoft.com/library/23a20143-241d-4fe5-9d9f-3933fd594c03) and [NIB: Named Permission Sets](http://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).</span></span>  
  
 <span data-ttu-id="d651e-112">拡張オブジェクトが返すデータ型は、4 つの基本 XPath データ型である `number`、`string`、`Boolean`、および `node set` のうちのいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="d651e-112">The data types returned from extension objects are one of the four basic XPath data types of `number`, `string`, `Boolean`, and `node set`.</span></span>  
  
 <span data-ttu-id="d651e-113">現在、`params` キーワードを使用して定義されるメソッド (不特定数のパラメーターを渡すことができる) は、<xref:System.Xml.Xsl.XslCompiledTransform> クラスでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="d651e-113">Any method that is defined with the `params` keyword, which allows an unspecified number of parameters to be passed, is not currently supported by the <xref:System.Xml.Xsl.XslCompiledTransform> class.</span></span> <span data-ttu-id="d651e-114">`params` キーワードを使用して定義されたメソッドを使用する XSLT スタイル シートは、正しく動作しません。</span><span class="sxs-lookup"><span data-stu-id="d651e-114">XSLT style sheets that utilize any method defined with the `params` keyword will not work correctly.</span></span> <span data-ttu-id="d651e-115">詳細については、[params](~/docs/csharp/language-reference/keywords/params.md) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d651e-115">For details, see [params](~/docs/csharp/language-reference/keywords/params.md).</span></span>  
  
### <a name="to-use-an-xslt-extension-object"></a><span data-ttu-id="d651e-116">XSLT 拡張オブジェクトを使用するために必要な処理</span><span class="sxs-lookup"><span data-stu-id="d651e-116">To use an XSLT extension object</span></span>  
  
1.  <span data-ttu-id="d651e-117"><xref:System.Xml.Xsl.XsltArgumentList> オブジェクトを作成し、<xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> メソッドを使用して拡張オブジェクトを追加します。</span><span class="sxs-lookup"><span data-stu-id="d651e-117">Create an <xref:System.Xml.Xsl.XsltArgumentList> object and add the extension object using <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A> method.</span></span>  
  
2.  <span data-ttu-id="d651e-118">スタイル シートから拡張オブジェクトを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d651e-118">Call the extension object from the style sheet.</span></span>  
  
3.  <span data-ttu-id="d651e-119"><xref:System.Xml.Xsl.XsltArgumentList> オブジェクトを <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="d651e-119">Pass the <xref:System.Xml.Xsl.XsltArgumentList> object to the <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A> method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d651e-120">参照</span><span class="sxs-lookup"><span data-stu-id="d651e-120">See Also</span></span>  
 [<span data-ttu-id="d651e-121">XSLT 変換</span><span class="sxs-lookup"><span data-stu-id="d651e-121">XSLT Transformations</span></span>](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [<span data-ttu-id="d651e-122">XSLT のセキュリティに関する考慮事項</span><span class="sxs-lookup"><span data-stu-id="d651e-122">XSLT Security Considerations</span></span>](../../../../docs/standard/data/xml/xslt-security-considerations.md)
