---
title: "型の式&lt;型&gt;はクエリ不可能"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords: BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f2b98bf48f0b3965929f9211c2944ff97754f23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a><span data-ttu-id="499dc-102">型の式&lt;型&gt;はクエリ不可能</span><span class="sxs-lookup"><span data-stu-id="499dc-102">Expression of type &lt;type&gt; is not queryable</span></span>
<span data-ttu-id="499dc-103">型の式\<型 > はクエリ不可能です。</span><span class="sxs-lookup"><span data-stu-id="499dc-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="499dc-104">LINQ プロバイダーに対してアセンブリ参照や名前空間インポートが不足していないを確認してください。</span><span class="sxs-lookup"><span data-stu-id="499dc-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="499dc-105">クエリ可能型が定義されている、 <xref:System.Linq>、 <xref:System.Data.Linq>、および<xref:System.Xml.Linq>名前空間。</span><span class="sxs-lookup"><span data-stu-id="499dc-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="499dc-106">1 つ以上の LINQ クエリを実行するこれらの名前空間をインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="499dc-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="499dc-107"><xref:System.Linq>名前空間を有効にするオブジェクトに対してクエリをコレクションや配列などに LINQ を使用しています。</span><span class="sxs-lookup"><span data-stu-id="499dc-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="499dc-108"><xref:System.Data.Linq>名前空間では、LINQ を使用して SQL Server データベースと ADO.NET データセットのクエリを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="499dc-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="499dc-109"><xref:System.Xml.Linq>名前空間を使用すると XML のクエリに LINQ を使用して、Visual Basic で XML 機能を使用するとします。</span><span class="sxs-lookup"><span data-stu-id="499dc-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="499dc-110">**エラー ID:** BC36593</span><span class="sxs-lookup"><span data-stu-id="499dc-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="499dc-111">このエラーを解決するには</span><span class="sxs-lookup"><span data-stu-id="499dc-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="499dc-112">追加、`Import`のステートメント、 <xref:System.Linq>、 <xref:System.Data.Linq>、または<xref:System.Xml.Linq>をコード ファイルの名前空間。</span><span class="sxs-lookup"><span data-stu-id="499dc-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="499dc-113">使用して、プロジェクトの名前空間をインポートすることも、**参照**、プロジェクト デザイナーのページ (**My Project**)。</span><span class="sxs-lookup"><span data-stu-id="499dc-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2.  <span data-ttu-id="499dc-114">クエリのソースはクエリ可能型として指定した型を確認してください。</span><span class="sxs-lookup"><span data-stu-id="499dc-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="499dc-115">実装する型は、<xref:System.Collections.Generic.IEnumerable%601>または<xref:System.Linq.IQueryable%601>です。</span><span class="sxs-lookup"><span data-stu-id="499dc-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="499dc-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="499dc-116">See Also</span></span>  
 <xref:System.Linq>  
 <xref:System.Data.Linq>  
 <xref:System.Xml.Linq>  
 [<span data-ttu-id="499dc-117">Visual Basic における LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="499dc-117">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="499dc-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="499dc-118">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [<span data-ttu-id="499dc-119">XML</span><span class="sxs-lookup"><span data-stu-id="499dc-119">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="499dc-120">参照と Imports ステートメント</span><span class="sxs-lookup"><span data-stu-id="499dc-120">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [<span data-ttu-id="499dc-121">Imports ステートメント (.NET 名前空間および型)</span><span class="sxs-lookup"><span data-stu-id="499dc-121">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 <span data-ttu-id="499dc-122">[[参照設定] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="499dc-122">[References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span></span>
