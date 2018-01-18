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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: bb6f8683ce49c8115b6dce477d0e61369d7abeef
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="creating-the-object-model"></a><span data-ttu-id="11ff4-102">オブジェクト モデルの作成</span><span class="sxs-lookup"><span data-stu-id="11ff4-102">Creating the Object Model</span></span>
<span data-ttu-id="11ff4-103">既存のデータベースからオブジェクト モデルを作成し、このオブジェクト モデルを既定の状態で使用できます。</span><span class="sxs-lookup"><span data-stu-id="11ff4-103">You can create your object model from an existing database and use the model in its default state.</span></span> <span data-ttu-id="11ff4-104">オブジェクト モデルの多くの側面と動作をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="11ff4-104">You can also customize many aspects of the model and its behavior.</span></span>  
  
 <span data-ttu-id="11ff4-105">使用している場合[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]、使用することができます、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]オブジェクト モデルを作成します。</span><span class="sxs-lookup"><span data-stu-id="11ff4-105">If you are using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], you can use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to create your object model.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11ff4-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="11ff4-106">In This Section</span></span>  
 [<span data-ttu-id="11ff4-107">方法: Visual Basic または C# でオブジェクト モデルを生成する</span><span class="sxs-lookup"><span data-stu-id="11ff4-107">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 <span data-ttu-id="11ff4-108">SQLMetal コマンド ライン ツールの使い方について説明します。</span><span class="sxs-lookup"><span data-stu-id="11ff4-108">Describes how to use the SQLMetal command-line tool.</span></span> <span data-ttu-id="11ff4-109">また、[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] ユーザー向けの[!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)]に関するトピックへのリンクを示します。</span><span class="sxs-lookup"><span data-stu-id="11ff4-109">Also provides a link to the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] for [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] users</span></span>  
  
 [<span data-ttu-id="11ff4-110">方法 : オブジェクト モデルを外部ファイルとして生成する</span><span class="sxs-lookup"><span data-stu-id="11ff4-110">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)  
 <span data-ttu-id="11ff4-111">属性ベースの対応付けを使用する代わりに外部マッピング ファイルを生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="11ff4-111">Describes how to generate an external mapping file instead of using attribute-based mapping.</span></span>  
  
 [<span data-ttu-id="11ff4-112">方法 : DBML ファイルを変更してカスタマイズ コードを生成する</span><span class="sxs-lookup"><span data-stu-id="11ff4-112">How to: Generate Customized Code by Modifying a DBML File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-customized-code-by-modifying-a-dbml-file.md)  
 <span data-ttu-id="11ff4-113">[!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] または C# のコードを DBML メタデータ ファイルから生成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="11ff4-113">Describes how to generate [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] or C# code from a DBML metadata file.</span></span>  
  
 [<span data-ttu-id="11ff4-114">方法 : DBML ファイルおよび外部マッピング ファイルを検証する</span><span class="sxs-lookup"><span data-stu-id="11ff4-114">How to: Validate DBML and External Mapping Files</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)  
 <span data-ttu-id="11ff4-115">変更したマッピング ファイルを検証する方法について説明します (上級)。</span><span class="sxs-lookup"><span data-stu-id="11ff4-115">Describes how to validate mapping files that you have modified (advanced).</span></span>  
  
 [<span data-ttu-id="11ff4-116">方法 : エンティティをシリアル化可能にする</span><span class="sxs-lookup"><span data-stu-id="11ff4-116">How to: Make Entities Serializable</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)  
 <span data-ttu-id="11ff4-117">適切な属性を追加してエンティティをシリアル化可能にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="11ff4-117">Describes how to add appropriate attributes to make entities serializable.</span></span>  
  
 [<span data-ttu-id="11ff4-118">方法 : コード エディターを使用してエンティティ クラスをカスタマイズする</span><span class="sxs-lookup"><span data-stu-id="11ff4-118">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)  
 <span data-ttu-id="11ff4-119">コード エディターを使用して、独自のマッピング コードを書いたり、自動的に生成されたコードをカスタマイズしたりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="11ff4-119">Describes how to use the code editor to write your own mapping code, or customize code that has been autogenerated.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="11ff4-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="11ff4-120">Related Sections</span></span>  
 [<span data-ttu-id="11ff4-121">LINQ to SQL オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="11ff4-121">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 <span data-ttu-id="11ff4-122">詳細について説明、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]オブジェクト モデルです。</span><span class="sxs-lookup"><span data-stu-id="11ff4-122">Provides details about the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="11ff4-123">一般的な LINQ to SQL の使用手順</span><span class="sxs-lookup"><span data-stu-id="11ff4-123">Typical Steps for Using LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/typical-steps-for-using-linq-to-sql.md)  
 <span data-ttu-id="11ff4-124">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] アプリケーションを実装する標準的な手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="11ff4-124">Explains the typical steps that you follow to implement a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] application.</span></span>
