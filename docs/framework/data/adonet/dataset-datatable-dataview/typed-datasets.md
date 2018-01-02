---
title: "型指定されたデータセット"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 033d2548-cf24-4c05-8179-67d8b009c048
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6ede928352c9e0f02f6ad4c27ce8f5347b868986
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="typed-datasets"></a><span data-ttu-id="881e1-102">型指定されたデータセット</span><span class="sxs-lookup"><span data-stu-id="881e1-102">Typed DataSets</span></span>
<span data-ttu-id="881e1-103">厳密に型指定されていない変数を使用した値への遅延バインディング アクセスに加えて、<xref:System.Data.DataSet> には、厳密に型指定された変数を使用したデータへのアクセスも用意されています。</span><span class="sxs-lookup"><span data-stu-id="881e1-103">Along with late bound access to values through weakly typed variables, the <xref:System.Data.DataSet> provides access to data through a strongly typed metaphor.</span></span> <span data-ttu-id="881e1-104">テーブルと列の一部であるが、**データセット**わかりやすい名前を使用してアクセスできる、厳密に型指定される変数です。</span><span class="sxs-lookup"><span data-stu-id="881e1-104">Tables and columns that are part of the **DataSet** can be accessed using user-friendly names and strongly typed variables.</span></span>  
  
 <span data-ttu-id="881e1-105">型指定された**データセット**から派生したクラスには、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="881e1-105">A typed **DataSet** is a class that derives from a **DataSet**.</span></span> <span data-ttu-id="881e1-106">すべてのメソッド、イベント、およびのプロパティを継承など、**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="881e1-106">As such, it inherits all the methods, events, and properties of a **DataSet**.</span></span> <span data-ttu-id="881e1-107">さらに、型指定された**データセット**厳密に型指定されたメソッド、イベント、およびプロパティを提供します。</span><span class="sxs-lookup"><span data-stu-id="881e1-107">Additionally, a typed **DataSet** provides strongly typed methods, events, and properties.</span></span> <span data-ttu-id="881e1-108">つまり、コレクションベースのメソッドを使用せずに名前でテーブルおよび列にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="881e1-108">This means you can access tables and columns by name, instead of using collection-based methods.</span></span> <span data-ttu-id="881e1-109">別に、型指定された、コードの読みやすさが向上**データセット**もにより、Visual Studio .NET コード エディターに入力すると、行を自動的に完了します。</span><span class="sxs-lookup"><span data-stu-id="881e1-109">Aside from the improved readability of the code, a typed **DataSet** also allows the Visual Studio .NET code editor to automatically complete lines as you type.</span></span>  
  
 <span data-ttu-id="881e1-110">さらに、厳密に型指定された**データセット**コンパイル時に適切な型の値へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="881e1-110">Additionally, the strongly typed **DataSet** provides access to values as the correct type at compile time.</span></span> <span data-ttu-id="881e1-111">厳密に型指定と**データセット**コードがコンパイルではなく実行時に時に、型の不一致エラーはキャッチされます。</span><span class="sxs-lookup"><span data-stu-id="881e1-111">With a strongly typed **DataSet**, type mismatch errors are caught when the code is compiled rather than at run time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="881e1-112">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="881e1-112">In This Section</span></span>  
 [<span data-ttu-id="881e1-113">厳密に型指定された DataSet の生成</span><span class="sxs-lookup"><span data-stu-id="881e1-113">Generating Strongly Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-strongly-typed-datasets.md)  
 <span data-ttu-id="881e1-114">作成し、厳密に型指定を使用する方法について説明**データセット**です。</span><span class="sxs-lookup"><span data-stu-id="881e1-114">Describes how to create and use a strongly typed **DataSet**.</span></span>  
  
 [<span data-ttu-id="881e1-115">型指定された DataSet の注釈</span><span class="sxs-lookup"><span data-stu-id="881e1-115">Annotating Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/annotating-typed-datasets.md)  
 <span data-ttu-id="881e1-116">厳密に型を生成するために使用する XML スキーマ定義言語 (XSD) スキーマの注釈を設定する方法について説明**データセット**して**データセット**基になるスキーマを変更することがなく要素に表示名。</span><span class="sxs-lookup"><span data-stu-id="881e1-116">Describes how to annotate the XML Schema definition language (XSD) schema used to generate a strongly typed **DataSet**, to give **DataSet** elements friendly names without altering the underlying schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="881e1-117">参照</span><span class="sxs-lookup"><span data-stu-id="881e1-117">See Also</span></span>  
 [<span data-ttu-id="881e1-118">DataSet、DataTable、および DataView</span><span class="sxs-lookup"><span data-stu-id="881e1-118">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="881e1-119">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="881e1-119">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
