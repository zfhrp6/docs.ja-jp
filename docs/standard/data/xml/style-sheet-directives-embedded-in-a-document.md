---
title: "ドキュメントに埋め込まれたスタイル シート ディレクティブ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d79fb295-ebc7-438d-ba1b-05be7d534834
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8c5cfcc9f35e4a07e9426a4dd24c1e2f04985f16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="style-sheet-directives-embedded-in-a-document"></a><span data-ttu-id="80c53-102">ドキュメントに埋め込まれたスタイル シート ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="80c53-102">Style Sheet Directives Embedded in a Document</span></span>
<span data-ttu-id="80c53-103">既存の XML に `<?xml:stylesheet?>` というスタイル シート ディレクティブが含まれていることがあります。</span><span class="sxs-lookup"><span data-stu-id="80c53-103">Occasionally, existing XML contains the style sheet directive of `<?xml:stylesheet?>`.</span></span> <span data-ttu-id="80c53-104">Microsoft Internet Explorer では、これを受け付ける代わりに、`<?xml-stylesheet?>`構文です。</span><span class="sxs-lookup"><span data-stu-id="80c53-104">Microsoft Internet Explorer accepts this as an alternative to the `<?xml-stylesheet?>` syntax.</span></span> <span data-ttu-id="80c53-105">次のように `<?xml:stylesheet?>` ディレクティブが含まれている XML データを XML ドキュメント オブジェクト モデル (DOM) に読み込もうとすると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="80c53-105">When the XML data contains an `<?xml:stylesheet?>` directive, as shown in the following data, attempting to load this data into the XML Document Object Model (DOM) throws an exception.</span></span>  
  
```xml  
<?xml version="1.0" ?>  
<?xml:stylesheet type="text/xsl" href="test2.xsl"?>  
<root>  
    <test>Node 1</test>  
    <test>Node 2</test>  
</root>  
```  
  
 <span data-ttu-id="80c53-106">これは、ために発生、`<?xml:stylesheet?>`が無効と見なされます**ProcessingInstruction** DOM に</span><span class="sxs-lookup"><span data-stu-id="80c53-106">This occurs because the `<?xml:stylesheet?>` is considered an invalid **ProcessingInstruction** to the DOM.</span></span> <span data-ttu-id="80c53-107">どの**ProcessingInstruction**、namespaces in XML 』 仕様ではなく修飾名 (Qname)、コロンを含まない名前 (NCNames) を指定できますのみです。</span><span class="sxs-lookup"><span data-stu-id="80c53-107">Any **ProcessingInstruction**, according to the Namespaces in XML specification, can only be no-colon names (NCNames), as opposed to qualified names (QNames).</span></span>  
  
 <span data-ttu-id="80c53-108">In XML 』 仕様、効果が得名前空間のセクション 6、**ロード**と**LoadXml**に準拠しているメソッドの仕様を文書内にあります。</span><span class="sxs-lookup"><span data-stu-id="80c53-108">From Section 6 of the Namespaces in XML specification, the effect of having the **Load** and **LoadXml** methods conform to the specification is that in a document:</span></span>  
  
-   <span data-ttu-id="80c53-109">すべての要素型と属性名は、0 個または 1 個のコロンを含みます。</span><span class="sxs-lookup"><span data-stu-id="80c53-109">All element types and attribute names contain either zero or one colon.</span></span>  
  
-   <span data-ttu-id="80c53-110">エンティティ名、処理命令ターゲット、記法名は、いずれもコロンを含みません。</span><span class="sxs-lookup"><span data-stu-id="80c53-110">No entity names, ProcessingInstruction targets, or notation names contain any colons.</span></span>  
  
 <span data-ttu-id="80c53-111">コロンが含まれた `<?xml:stylesheet?>` は、2 番目の規則に違反します。</span><span class="sxs-lookup"><span data-stu-id="80c53-111">With the `<?xml:stylesheet?>` containing a colon, you now violate the rule in the second bullet.</span></span>  
  
 <span data-ttu-id="80c53-112">www.w3.org/TR/xml-stylesheet で公開されている W3C (World Wide Web Consortium) 勧告『Associating Style Sheets with XML documents Version 1.0』によれば、XSLT スタイル シートを XML ドキュメントに関連付ける処理命令は、コロンをダッシュに置き換えた `<?xml-stylesheet?>` です。</span><span class="sxs-lookup"><span data-stu-id="80c53-112">According to the World Wide Web Consortium (W3C) Associating Style Sheets with XML documents Version 1.0 Recommendation, located at www.w3.org/TR/xml-stylesheet, the processing instruction to associate an XSLT style sheet with an XML document is `<?xml-stylesheet?>`, with a dash replacing the colon.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c53-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="80c53-113">See Also</span></span>  
 [<span data-ttu-id="80c53-114">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="80c53-114">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
