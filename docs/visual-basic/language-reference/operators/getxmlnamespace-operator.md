---
title: GetXmlNamespace 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: e21cf160d10f308990894d1a85c4f5d05b90f68d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603484"
---
# <a name="getxmlnamespace-operator-visual-basic"></a><span data-ttu-id="194fc-102">GetXmlNamespace 演算子 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="194fc-102">GetXmlNamespace Operator (Visual Basic)</span></span>
<span data-ttu-id="194fc-103">取得、<xref:System.Xml.Linq.XNamespace>指定された XML 名前空間プレフィックスに対応するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="194fc-103">Gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the specified XML namespace prefix.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="194fc-104">構文</span><span class="sxs-lookup"><span data-stu-id="194fc-104">Syntax</span></span>  
  
```  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a><span data-ttu-id="194fc-105">指定項目</span><span class="sxs-lookup"><span data-stu-id="194fc-105">Parts</span></span>  
 `xmlNamespacePrefix`  
 <span data-ttu-id="194fc-106">任意。</span><span class="sxs-lookup"><span data-stu-id="194fc-106">Optional.</span></span> <span data-ttu-id="194fc-107">XML 名前空間プレフィックスを識別する文字列。</span><span class="sxs-lookup"><span data-stu-id="194fc-107">The string that identifies the XML namespace prefix.</span></span> <span data-ttu-id="194fc-108">指定した場合、この文字列は有効な XML 識別子にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="194fc-108">If supplied, this string must be a valid XML identifier.</span></span> <span data-ttu-id="194fc-109">詳細については、次を参照してください。[宣言されている XML 要素の名前および属性](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)です。</span><span class="sxs-lookup"><span data-stu-id="194fc-109">For more information, see [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).</span></span> <span data-ttu-id="194fc-110">プレフィックスが指定されていない場合は、既定の名前空間が返されます。</span><span class="sxs-lookup"><span data-stu-id="194fc-110">If no prefix is specified, the default namespace is returned.</span></span> <span data-ttu-id="194fc-111">既定の名前空間が指定されていない場合は、空の名前空間が返されます。</span><span class="sxs-lookup"><span data-stu-id="194fc-111">If no default namespace is specified, the empty namespace is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="194fc-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="194fc-112">Return Value</span></span>  
 <span data-ttu-id="194fc-113"><xref:System.Xml.Linq.XNamespace> XML 名前空間プレフィックスに対応するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="194fc-113">The <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="194fc-114">コメント</span><span class="sxs-lookup"><span data-stu-id="194fc-114">Remarks</span></span>  
 <span data-ttu-id="194fc-115">`GetXmlNamespace`演算子を取得、<xref:System.Xml.Linq.XNamespace>オブジェクト XML 名前空間プレフィックスに対応する`xmlNamespacePrefix`です。</span><span class="sxs-lookup"><span data-stu-id="194fc-115">The `GetXmlNamespace` operator gets the <xref:System.Xml.Linq.XNamespace> object that corresponds to the XML namespace prefix `xmlNamespacePrefix`.</span></span>  
  
 <span data-ttu-id="194fc-116">XML リテラルおよび XML 軸のプロパティで直接 XML 名前空間プレフィックスを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="194fc-116">You can use XML namespace prefixes directly in XML literals and XML axis properties.</span></span> <span data-ttu-id="194fc-117">ただし、使用する必要があります、`GetXmlNamespace`に名前空間プレフィックスを変換する演算子、<xref:System.Xml.Linq.XNamespace>オブジェクトの前に、コードで使用することができます。</span><span class="sxs-lookup"><span data-stu-id="194fc-117">However, you must use the `GetXmlNamespace` operator to convert a namespace prefix to an <xref:System.Xml.Linq.XNamespace> object before you can use it in your code.</span></span> <span data-ttu-id="194fc-118">修飾されていない要素名を追加することができます、<xref:System.Xml.Linq.XNamespace>完全修飾を取得するオブジェクト<xref:System.Xml.Linq.XName>オブジェクト、どの多[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]メソッドを必要とします。</span><span class="sxs-lookup"><span data-stu-id="194fc-118">You can append an unqualified element name to an <xref:System.Xml.Linq.XNamespace> object to get a fully qualified <xref:System.Xml.Linq.XName> object, which many [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] methods require.</span></span>  
  
## <a name="example"></a><span data-ttu-id="194fc-119">例</span><span class="sxs-lookup"><span data-stu-id="194fc-119">Example</span></span>  
 <span data-ttu-id="194fc-120">次の例ではインポート`ns`XML 名前空間プレフィックスとして。</span><span class="sxs-lookup"><span data-stu-id="194fc-120">The following example imports `ns` as an XML namespace prefix.</span></span> <span data-ttu-id="194fc-121">XML リテラルを作成し、修飾名を持つ最初の子ノードにアクセスする、名前空間のプレフィックスを使用して`ns:phone`です。</span><span class="sxs-lookup"><span data-stu-id="194fc-121">It then uses the prefix of the namespace to create an XML literal and access the first child node that has the qualified name `ns:phone`.</span></span> <span data-ttu-id="194fc-122">これは、後、その子ノードを渡します、`ShowName`を使用して、修飾名を構築するサブルーチン、`GetXmlNamespace`演算子。</span><span class="sxs-lookup"><span data-stu-id="194fc-122">It then passes that child node to the `ShowName` subroutine, which constructs a qualified name by using the `GetXmlNamespace` operator.</span></span> <span data-ttu-id="194fc-123">`ShowName`修飾名を渡しますサブルーチン、<xref:System.Xml.Linq.XNode.Ancestors%2A>親を取得するメソッド`ns:contact`ノード。</span><span class="sxs-lookup"><span data-stu-id="194fc-123">The `ShowName` subroutine then passes the qualified name to the <xref:System.Xml.Linq.XNode.Ancestors%2A> method to get the parent `ns:contact` node.</span></span>  
  
 [!code-vb[VbXMLSamples#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/getxmlnamespace-operator_1.vb)]  
  
 <span data-ttu-id="194fc-124">呼び出すと`TestGetXmlNamespace.RunSample()`、次のテキストを含むメッセージ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="194fc-124">When you call `TestGetXmlNamespace.RunSample()`, it displays a message box that contains the following text:</span></span>  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a><span data-ttu-id="194fc-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="194fc-125">See Also</span></span>  
 [<span data-ttu-id="194fc-126">Imports ステートメント (XML 名前空間)</span><span class="sxs-lookup"><span data-stu-id="194fc-126">Imports Statement (XML Namespace)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)  
 [<span data-ttu-id="194fc-127">Visual Basic での XML へのアクセス</span><span class="sxs-lookup"><span data-stu-id="194fc-127">Accessing XML in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
