---
title: "モデリングとマッピング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec8a9515-3708-4cde-a688-4d8e6975f150
caps.latest.revision: "7"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 2004b950f1096f574734259ba02944577dd9adc9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="modeling-and-mapping"></a><span data-ttu-id="f1679-102">モデリングとマッピング</span><span class="sxs-lookup"><span data-stu-id="f1679-102">Modeling and Mapping</span></span>
<span data-ttu-id="f1679-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] では、概念モデル、ストレージ モデル、およびこの 2 つのモデル間のマッピングをアプリケーションに最適な方法で定義できます。</span><span class="sxs-lookup"><span data-stu-id="f1679-103">In the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)], you can define the conceptual model, storage model, and the mapping between the two in the way that best suits your application.</span></span> <span data-ttu-id="f1679-104">Entity Data Model ツール[!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)]を作成することは、[ 。edmx ファイル](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)データベースまたはグラフィカルなモデルと、更新データベースまたはモデルのいずれかが変更されたときにこのファイルからです。</span><span class="sxs-lookup"><span data-stu-id="f1679-104">The Entity Data Model Tools in [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] allow you to create an .[edmx file](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4) from a database or a graphical model and then update that file when either the database or model changes.</span></span>  
  
 <span data-ttu-id="f1679-105">Entity Framework 4.1 以降では、Code First の開発を使用してモデルをプログラムで作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1679-105">Starting with the Entity Framework 4.1 you can also create a model programmatically using Code First development.</span></span> <span data-ttu-id="f1679-106">Code First の開発に対しては、2 つの異なるシナリオがあります。</span><span class="sxs-lookup"><span data-stu-id="f1679-106">There are two different scenarios for Code First development.</span></span> <span data-ttu-id="f1679-107">どちらの場合でも、開発者は .NET Framework のクラス定義をコーディングしてモデルを定義し、データ注釈または Fluent API を使用してオプションで追加のマッピングまたは構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="f1679-107">In both cases, the developer defines a model by coding .NET Framework class definitions, and then optionally specifies additional mapping or configuration by using Data Annotations or the fluent API.</span></span>  
  
 <span data-ttu-id="f1679-108">詳細については、次を参照してください。[マッピングの概念モデルの作成と](http://go.microsoft.com/fwlink/?LinkId=235016)です。</span><span class="sxs-lookup"><span data-stu-id="f1679-108">For more information, see [Creating and Mapping a Conceptual Model](http://go.microsoft.com/fwlink/?LinkId=235016).</span></span>  
  
 <span data-ttu-id="f1679-109">含まれている EDM のジェネレーターを使用することも、[!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="f1679-109">You can also use the EDM Generator, which is included with the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="f1679-110">EdmGen.exe は、既存のデータ ソースから .csdl ファイル、.ssdl ファイル、および .msl ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="f1679-110">The EdmGen.exe generates the .csdl, .ssdl, and .msl files from an existing data source.</span></span> <span data-ttu-id="f1679-111">モデルとマッピングの内容を手動で作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="f1679-111">You can also manually create the model and mapping content.</span></span> <span data-ttu-id="f1679-112">詳細については、次を参照してください。 [EDM ジェネレーター (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="f1679-112">For more information, see [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).</span></span>
