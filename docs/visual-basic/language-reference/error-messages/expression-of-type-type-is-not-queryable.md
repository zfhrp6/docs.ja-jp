---
title: "型の式&lt;型&gt;クエリ不可能です。Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36593
- vbc36593
dev_langs:
- VB
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: 5
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
ms.openlocfilehash: 84563c7339ffe7415017280d74a13d6501236da5
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a><span data-ttu-id="19bc6-102">型の式&lt;型&gt;クエリ不可能です</span><span class="sxs-lookup"><span data-stu-id="19bc6-102">Expression of type &lt;type&gt; is not queryable</span></span>
<span data-ttu-id="19bc6-103">型の式\<型 > クエリ不可能です。</span><span class="sxs-lookup"><span data-stu-id="19bc6-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="19bc6-104">LINQ プロバイダーに対してアセンブリ参照や名前空間インポートを不足していないことを確認します。</span><span class="sxs-lookup"><span data-stu-id="19bc6-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="19bc6-105">クエリ可能型が定義されている、 <xref:System.Linq>、 <xref:System.Data.Linq>、および<xref:System.Xml.Linq>名前空間</xref:System.Xml.Linq></xref:System.Data.Linq></xref:System.Linq>。</span><span class="sxs-lookup"><span data-stu-id="19bc6-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="19bc6-106">1 つ以上の LINQ クエリを実行するこれらの名前空間をインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="19bc6-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="19bc6-107"><xref:System.Linq>名前空間は、コレクションと配列などのクエリ オブジェクトを LINQ を使用しています</xref:System.Linq>。</span><span class="sxs-lookup"><span data-stu-id="19bc6-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="19bc6-108"><xref:System.Data.Linq>名前空間では、LINQ を使用して、ADO.NET データセットと SQL Server データベースを照会することができます</xref:System.Data.Linq>。</span><span class="sxs-lookup"><span data-stu-id="19bc6-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="19bc6-109"><xref:System.Xml.Linq>名前空間を使用すると XML のクエリに LINQ を使用して、Visual Basic で XML 機能を使用します</xref:System.Xml.Linq>。</span><span class="sxs-lookup"><span data-stu-id="19bc6-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="19bc6-110">**エラー ID:** BC36593</span><span class="sxs-lookup"><span data-stu-id="19bc6-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="19bc6-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="19bc6-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="19bc6-112">追加、`Import`のステートメント、 <xref:System.Linq>、 <xref:System.Data.Linq>、または<xref:System.Xml.Linq>をコード ファイルの名前空間</xref:System.Xml.Linq></xref:System.Data.Linq></xref:System.Linq>。</span><span class="sxs-lookup"><span data-stu-id="19bc6-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="19bc6-113">使用して、プロジェクトの名前空間をインポートすることも、**参照**プロジェクト デザイナーのページ (**My Project**)。</span><span class="sxs-lookup"><span data-stu-id="19bc6-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2.  <span data-ttu-id="19bc6-114">クエリのソースがクエリ可能型として指定した型を確認します。</span><span class="sxs-lookup"><span data-stu-id="19bc6-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="19bc6-115">つまり<xref:System.Collections.Generic.IEnumerable%601>、または<xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601></xref:System.Collections.Generic.IEnumerable%601>を実装する型</span><span class="sxs-lookup"><span data-stu-id="19bc6-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19bc6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="19bc6-116">See Also</span></span>  
 <span data-ttu-id="19bc6-117"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="19bc6-117"><xref:System.Linq></span></span>   
 <span data-ttu-id="19bc6-118"><xref:System.Data.Linq></xref:System.Data.Linq></span><span class="sxs-lookup"><span data-stu-id="19bc6-118"><xref:System.Data.Linq></span></span>   
 <span data-ttu-id="19bc6-119"><xref:System.Xml.Linq></span><span class="sxs-lookup"><span data-stu-id="19bc6-119"><xref:System.Xml.Linq></span></span>   
<span data-ttu-id="19bc6-120"> [Visual Basic における LINQ の概要](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="19bc6-120"> [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="19bc6-121"> [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="19bc6-121"> [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="19bc6-122"> [XML](../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="19bc6-122"> [XML](../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="19bc6-123"> [参照と Imports ステートメント](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span><span class="sxs-lookup"><span data-stu-id="19bc6-123"> [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span></span>  
<span data-ttu-id="19bc6-124"> [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="19bc6-124"> [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="19bc6-125"> [[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="19bc6-125"> [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span></span>
