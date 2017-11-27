---
title: "オブジェクト モデルの作成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27afce86-9b1d-45fb-8e0b-636bf671a236
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c933e7e2871d0a72e8e10a25d94e9d458cdd1d43
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="creating-the-object-model"></a><span data-ttu-id="376aa-102">オブジェクト モデルの作成</span><span class="sxs-lookup"><span data-stu-id="376aa-102">Creating the Object Model</span></span>
<span data-ttu-id="376aa-103">既存のデータベースからオブジェクト モデルを作成し、このオブジェクト モデルを既定の状態で使用できます。</span><span class="sxs-lookup"><span data-stu-id="376aa-103">You can create your object model from an existing database and use the model in its default state.</span></span> <span data-ttu-id="376aa-104">オブジェクト モデルの多くの側面と動作をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="376aa-104">You can also customize many aspects of the model and its behavior.</span></span>  
  
 <span data-ttu-id="376aa-105">使用している場合[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]、使用することができます、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]オブジェクト モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="376aa-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="376aa-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="376aa-106">In This Section</span></span>  
 [<span data-ttu-id="376aa-107">方法: Visual Basic または c# でのオブジェクト モデルの生成</span><span class="sxs-lookup"><span data-stu-id="376aa-107">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 <span data-ttu-id="376aa-108">SQLMetal コマンド ライン ツールの使い方について説明します。</span><span class="sxs-lookup"><span data-stu-id="376aa-108">Describes how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="376aa-109">また、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ユーザー向けの[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]に関するトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="376aa-109">Also provides a link to the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] users</span></span>  
  
 [<span data-ttu-id="376aa-110">方法: 外部ファイルとしてオブジェクト モデルを生成します。</span><span class="sxs-lookup"><span data-stu-id="376aa-110">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)  
 <span data-ttu-id="376aa-111">属性ベースの対応付けを使用する代わりに外部マッピング ファイルを生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="376aa-111">Describes how to generate an external mapping file instead of using attribute-based mapping.</span></span>  
  
 [<span data-ttu-id="376aa-112">方法: DBML ファイルを変更してカスタマイズ コードを生成</span><span class="sxs-lookup"><span data-stu-id="376aa-112">How to: Generate Customized Code by Modifying a DBML File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-customized-code-by-modifying-a-dbml-file.md)  
 <span data-ttu-id="376aa-113">[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] または C# のコードを DBML メタデータ ファイルから生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="376aa-113">Describes how to generate [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# code from a DBML metadata file.</span></span>  
  
 [<span data-ttu-id="376aa-114">方法: DBML ファイルおよび外部マッピング ファイルの検証</span><span class="sxs-lookup"><span data-stu-id="376aa-114">How to: Validate DBML and External Mapping Files</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)  
 <span data-ttu-id="376aa-115">変更したマッピング ファイルを検証する方法について説明します (上級)。</span><span class="sxs-lookup"><span data-stu-id="376aa-115">Describes how to validate mapping files that you have modified (advanced).</span></span>  
  
 [<span data-ttu-id="376aa-116">方法: エンティティをシリアル化</span><span class="sxs-lookup"><span data-stu-id="376aa-116">How to: Make Entities Serializable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)  
 <span data-ttu-id="376aa-117">適切な属性を追加してエンティティをシリアル化可能にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="376aa-117">Describes how to add appropriate attributes to make entities serializable.</span></span>  
  
 [<span data-ttu-id="376aa-118">方法: コード エディターを使用してエンティティ クラスをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="376aa-118">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 <span data-ttu-id="376aa-119">コード エディターを使用して、独自のマッピング コードを書いたり、自動的に生成されたコードをカスタマイズしたりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="376aa-119">Describes how to use the code editor to write your own mapping code, or customize code that has been autogenerated.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="376aa-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="376aa-120">Related Sections</span></span>  
 [<span data-ttu-id="376aa-121">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="376aa-121">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 <span data-ttu-id="376aa-122">詳細について説明、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]オブジェクト モデルです。</span><span class="sxs-lookup"><span data-stu-id="376aa-122">Provides details about the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="376aa-123">LINQ to SQL を使用するための一般的な手順</span><span class="sxs-lookup"><span data-stu-id="376aa-123">Typical Steps for Using LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md)  
 <span data-ttu-id="376aa-124">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションを実装する標準的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="376aa-124">Explains the typical steps that you follow to implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application.</span></span>
