---
title: "GetXmlNamespace 演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
dev_langs:
- VB
helpviewer_keywords:
- GetXmlNamespace operator
- GetXmlNamespace keyword
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d6f977ab8c0b7dfb2dee936436ef4ec8530ba8f6
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="137cf-102">GetXmlNamespace 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="137cf-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="137cf-103">取得、<xref:System.Xml.Linq.XNamespace>指定された XML 名前空間プレフィックスに対応するオブジェクト</xref:System.Xml.Linq.XNamespace>。</span><span class="sxs-lookup"><span data-stu-id="137cf-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="137cf-104">構文</span><span class="sxs-lookup"><span data-stu-id="137cf-104">Syntax</span></span>  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="137cf-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="137cf-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="137cf-106">省略可能です。</span><span class="sxs-lookup"><span data-stu-id="137cf-106">Optional.</span></span> <span data-ttu-id="137cf-107">XML 名前空間プレフィックスを識別する文字列。</span><span class="sxs-lookup"><span data-stu-id="137cf-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="137cf-108">指定した場合、この文字列は有効な XML 識別子である必要があります。</span><span class="sxs-lookup"><span data-stu-id="137cf-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="137cf-109">詳細については、次を参照してください。[宣言されている XML 要素の名前と属性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)します。</span><span class="sxs-lookup"><span data-stu-id="137cf-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="137cf-110">プレフィックスが指定されていない場合は、既定の名前空間が返されます。</span><span class="sxs-lookup"><span data-stu-id="137cf-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="137cf-111">既定の名前空間が指定されていない場合は、空の名前空間が返されます。</span><span class="sxs-lookup"><span data-stu-id="137cf-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="137cf-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="137cf-112">Return Value</span></span>  
 <span data-ttu-id="137cf-113"><xref:System.Xml.Linq.XNamespace>XML 名前空間プレフィックスに対応するオブジェクト</xref:System.Xml.Linq.XNamespace>。</span><span class="sxs-lookup"><span data-stu-id="137cf-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="137cf-114">コメント</span><span class="sxs-lookup"><span data-stu-id="137cf-114">Remarks</span></span>  
 <span data-ttu-id="137cf-115">`GetXmlNamespace`演算子を取得、 <xref:System.Xml.Linq.XNamespace>XML 名前空間プレフィックスに対応するオブジェクト`xmlNamespacePrefix`</xref:System.Xml.Linq.XNamespace>。</span><span class="sxs-lookup"><span data-stu-id="137cf-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="137cf-116">XML リテラルと XML 軸プロパティに直接 XML 名前空間プレフィックスを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="137cf-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="137cf-117">ただし、使用する必要があります、`GetXmlNamespace`名前空間プレフィックスに変換する演算子、<xref:System.Xml.Linq.XNamespace>オブジェクトの前に、コードで使用することができます</xref:System.Xml.Linq.XNamespace>。</span><span class="sxs-lookup"><span data-stu-id="137cf-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="137cf-118">非修飾要素名を追加する、<xref:System.Xml.Linq.XNamespace>完全修飾を取得するオブジェクト<xref:System.Xml.Linq.XName>オブジェクトを指定[!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]メソッドが必要です</xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XNamespace>。</span><span class="sxs-lookup"><span data-stu-id="137cf-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="137cf-119">例</span><span class="sxs-lookup"><span data-stu-id="137cf-119">Example</span></span>  
 <span data-ttu-id="137cf-120">次の例ではインポート`ns`XML 名前空間プレフィックスとして。</span><span class="sxs-lookup"><span data-stu-id="137cf-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="137cf-121">使用して、名前空間のプレフィックスを XML リテラルを作成し、修飾名を持つ最初の子ノードにアクセス`ns:phone`します。</span><span class="sxs-lookup"><span data-stu-id="137cf-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="137cf-122">これは、後、その子ノードを渡します、`ShowName`を使用して、修飾名を構築するサブルーチン、`GetXmlNamespace`演算子。</span><span class="sxs-lookup"><span data-stu-id="137cf-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="137cf-123">`ShowName`サブルーチンは、修飾名を渡します、<xref:System.Xml.Linq.XNode.Ancestors%2A>親を取得するメソッド`ns:contact`ノード</xref:System.Xml.Linq.XNode.Ancestors%2A>。</span><span class="sxs-lookup"><span data-stu-id="137cf-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 <span data-ttu-id="137cf-124">[!code-vb[VbXMLSamples #&38;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="137cf-124">[!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="137cf-125">呼び出すと`TestGetXmlNamespace.RunSample()`、次のテキストを含むメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="137cf-125">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="137cf-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="137cf-126">See Also</span></span>  
 <span data-ttu-id="137cf-127">[Imports ステートメント (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span><span class="sxs-lookup"><span data-stu-id="137cf-127">[Imports Statement (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md) </span></span>  
<span data-ttu-id="137cf-128"> [Visual Basic における XML へのアクセス](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)</span><span class="sxs-lookup"><span data-stu-id="137cf-128"> [Accessing XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)</span></span>
