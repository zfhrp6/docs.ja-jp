---
title: "方法 : Visual Basic または C# でオブジェクト モデルを生成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0c73b33-5650-420c-b9dc-f49310c201ee
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 6ff5a314fb4264f57f1db3e8475a2e3105897f19
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-generate-the-object-model-in-visual-basic-or-c"></a><span data-ttu-id="a0cfc-102">方法 : Visual Basic または C# でオブジェクト モデルを生成する</span><span class="sxs-lookup"><span data-stu-id="a0cfc-102">How to: Generate the Object Model in Visual Basic or C#</span></span> #
<span data-ttu-id="a0cfc-103">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、使用しているプログラミング言語のオブジェクト モデルが、リレーショナル データベースに対応付けられています。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-103">In [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], an object model in your own programming language is mapped to a relational database.</span></span> <span data-ttu-id="a0cfc-104">2 つのツールが自動的に生成するために使用できる、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]または C# の場合、既存のデータベースのメタデータからモデル。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-104">Two tools are available for automatically generating a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# model from the metadata of an existing database.</span></span>  
  
-   <span data-ttu-id="a0cfc-105">[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] を使用している場合は、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]を使用してオブジェクト モデルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to generate an object model.</span></span> <span data-ttu-id="a0cfc-106">[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]生成するために豊富なユーザー インターフェイスを提供する[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]オブジェクト モデルです。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-106">The [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides a rich user interface to help you generate a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span> <span data-ttu-id="a0cfc-107">詳細については、「 [Linq to Visual Studio での SQL ツール](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)です。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-107">For more information see, [Linq to SQL Tools in Visual Studio](https://docs.microsoft.com/en-us/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>
  
-   <span data-ttu-id="a0cfc-108">SQLMetal コマンド ライン ツール。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-108">The SQLMetal command-line tool.</span></span> <span data-ttu-id="a0cfc-109">詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-109">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a0cfc-110">既存のデータベースがなく、オブジェクト モデルからデータベースを作成する場合は、コード エディターと <xref:System.Data.Linq.DataContext.CreateDatabase%2A> を使用してオブジェクト モデルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-110">If you do not have an existing database and want to create one from an object model, you can create your object model by using your code editor and <xref:System.Data.Linq.DataContext.CreateDatabase%2A>.</span></span> <span data-ttu-id="a0cfc-111">詳細については、次を参照してください。[する方法: データベースを動的に作成](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md)です。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-111">For more information, see [How to: Dynamically Create a Database](../../../../../../docs/framework/data/adonet/sql/linq/how-to-dynamically-create-a-database.md).</span></span>  
  
 <span data-ttu-id="a0cfc-112">ドキュメントを[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]を生成する方法の例を示します、[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]または c# のオブジェクト モデルを使用して、[!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-112">Documentation for the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] provides examples of how to generate a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# object model by using the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)].</span></span> <span data-ttu-id="a0cfc-113">以下の情報は、SQLMetal コマンド ライン ツールの使用方法の例です。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-113">The following information provide examples of how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="a0cfc-114">詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-114">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0cfc-115">例</span><span class="sxs-lookup"><span data-stu-id="a0cfc-115">Example</span></span>  
 <span data-ttu-id="a0cfc-116">次の例に示す SQLMetal コマンド ラインでは、Northwind サンプル データベースの属性ベースのオブジェクト モデルとして [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-116">The SQLMetal command line shown in the following example produces [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="a0cfc-117">ストアド プロシージャと関数も含まれます。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-117">Stored procedures and functions are also rendered.</span></span>  
  
```  
sqlmetal /code:northwind.vb /language:vb "c:\northwnd.mdf" /sprocs /functions  
```  
  
## <a name="example"></a><span data-ttu-id="a0cfc-118">例</span><span class="sxs-lookup"><span data-stu-id="a0cfc-118">Example</span></span>  
 <span data-ttu-id="a0cfc-119">次の例に示す SQLMetal コマンド ラインでは、Northwind サンプル データベースの属性ベースのオブジェクト モデルとして C# コードが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-119">The SQLMetal command line shown in the following example produces C# code as the attribute-based object model of the Northwind sample database.</span></span> <span data-ttu-id="a0cfc-120">ストアド プロシージャと関数も含まれ、テーブル名は自動的に複数化されます。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-120">Stored procedures and functions are also rendered, and table names are automatically pluralized.</span></span>  
  
```  
sqlmetal /code:northwind.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize  
```  
  
## <a name="see-also"></a><span data-ttu-id="a0cfc-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0cfc-121">See Also</span></span>  
 [<span data-ttu-id="a0cfc-122">プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="a0cfc-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 [<span data-ttu-id="a0cfc-123">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="a0cfc-123">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="a0cfc-124">チュートリアルによる学習</span><span class="sxs-lookup"><span data-stu-id="a0cfc-124">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="a0cfc-125">方法: コード エディターを使用してエンティティ クラスをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="a0cfc-125">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 [<span data-ttu-id="a0cfc-126">属性ベースのマッピング</span><span class="sxs-lookup"><span data-stu-id="a0cfc-126">Attribute-Based Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)  
 [<span data-ttu-id="a0cfc-127">SqlMetal.exe (コード生成ツール)</span><span class="sxs-lookup"><span data-stu-id="a0cfc-127">SqlMetal.exe (Code Generation Tool)</span></span>](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)  
 [<span data-ttu-id="a0cfc-128">外部マップ</span><span class="sxs-lookup"><span data-stu-id="a0cfc-128">External Mapping</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)  
 [<span data-ttu-id="a0cfc-129">サンプル データベースのダウンロード</span><span class="sxs-lookup"><span data-stu-id="a0cfc-129">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [<span data-ttu-id="a0cfc-130">オブジェクト モデルの作成</span><span class="sxs-lookup"><span data-stu-id="a0cfc-130">Creating the Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
