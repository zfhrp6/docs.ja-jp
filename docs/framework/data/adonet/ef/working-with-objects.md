---
title: "オブジェクトの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 338d8a55-05cc-46b0-bbb8-1379d77068e9
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 44dd517f08b4a408a0f7c70964c6bc53ca663afd
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="working-with-objects"></a><span data-ttu-id="42eae-102">オブジェクトの使用</span><span class="sxs-lookup"><span data-stu-id="42eae-102">Working with Objects</span></span>
<span data-ttu-id="42eae-103">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] では、エンティティ型のインスタンスである型指定された共通言語ランタイム (CLR) オブジェクトとして表現されたデータに対してクエリ、挿入、更新、削除を実行できます。</span><span class="sxs-lookup"><span data-stu-id="42eae-103">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] enables you to query, insert, update, and delete data, which is expressed as typed common language runtime (CLR) objects that are instances of entity types.</span></span> <span data-ttu-id="42eae-104">エンティティ型とは、概念モデルで定義されたエンティティのことです。</span><span class="sxs-lookup"><span data-stu-id="42eae-104">The entity types represent the entities defined in the conceptual model.</span></span> <span data-ttu-id="42eae-105">概念モデルで定義されたエンティティとリレーションシップが、[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] によってデータ ソースにマップされます。</span><span class="sxs-lookup"><span data-stu-id="42eae-105">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] maps entities and relationships that are defined in a conceptual model to a data source.</span></span> <span data-ttu-id="42eae-106">[!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]以下を実行する機能を提供します。 オブジェクトとしてデータ ソースから返されたデータを具体化以外の場合は、オブジェクトに加えられた変更の追跡です。 同時実行を処理以外の場合はオブジェクトの変更をデータ ソースを反映してオブジェクトをコントロールにバインドします。</span><span class="sxs-lookup"><span data-stu-id="42eae-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provides facilities to do the following: materialize data returned from the data source as objects; track changes that were made to the objects; handle concurrency; propagate object changes back to the data source; and bind objects to controls.</span></span>  
  
 <span data-ttu-id="42eae-107">Entity Framework は、「最新のバージョンでのオブジェクトを操作の詳細については[オブジェクトの操作](http://go.microsoft.com/fwlink/?LinkId=235289)です。</span><span class="sxs-lookup"><span data-stu-id="42eae-107">For more information about working with objects in the latest version of the Entity Framework see, [Working with Objects](http://go.microsoft.com/fwlink/?LinkId=235289).</span></span>
