---
title: "インスタンス エンコーディング オプション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89e4b029-4f68-438c-8117-9b21fe094ef4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7664eecb68ff9aec0f5e3e31aa08058700f0e92
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="instance-encoding-option"></a><span data-ttu-id="470c3-102">インスタンス エンコーディング オプション</span><span class="sxs-lookup"><span data-stu-id="470c3-102">Instance Encoding Option</span></span>
<span data-ttu-id="470c3-103">**インスタンス エンコーディング オプション**SQL Workflow Instance Store のプロパティを使用して、SQL 永続化プロバイダーが保存する前に GZip アルゴリズムを使用して、ワークフロー インスタンス状態情報を圧縮するかどうかを指定できます、永続性データベースに情報です。</span><span class="sxs-lookup"><span data-stu-id="470c3-103">The **Instance Encoding Option** property of the SQL Workflow Instance Store lets you specify whether the SQL persistence provider should compress the workflow instance state information using the GZip algorithm before saving the information into the persistence database.</span></span> <span data-ttu-id="470c3-104">このプロパティに使用できる値は GZip と None です。</span><span class="sxs-lookup"><span data-stu-id="470c3-104">The allowed values for this property are: GZip and None.</span></span> <span data-ttu-id="470c3-105">既定値は None です。</span><span class="sxs-lookup"><span data-stu-id="470c3-105">The default value is None.</span></span> <span data-ttu-id="470c3-106">これらのオプションを次の一覧で説明します。</span><span class="sxs-lookup"><span data-stu-id="470c3-106">The following list describes these options.</span></span>  
  
1.  <span data-ttu-id="470c3-107">**GZip**です。</span><span class="sxs-lookup"><span data-stu-id="470c3-107">**GZip**.</span></span> <span data-ttu-id="470c3-108">永続化プロバイダーは、永続性データベースに状態情報を永続化する前に、GZip アルゴリズムを使用して状態情報をエンコードします。</span><span class="sxs-lookup"><span data-stu-id="470c3-108">The persistence provider encodes the state information using the GZip algorithm before persisting the state information in the persistence database.</span></span>  
  
2.  <span data-ttu-id="470c3-109">**None**です。</span><span class="sxs-lookup"><span data-stu-id="470c3-109">**None**.</span></span> <span data-ttu-id="470c3-110">永続化プロバイダーは、永続性データベースに情報を保存する前は、状態情報をエンコードしません。</span><span class="sxs-lookup"><span data-stu-id="470c3-110">The persistence provider does not encode the state information before saving the information into the persistence database.</span></span>  
  
 <span data-ttu-id="470c3-111">GZip を使用してワークフロー インスタンスの状態情報をエンコードすると、SQL データベースのメモリ消費量が減ります。また、ワークフロー サービス ホストが実行されているコンピューターとは異なるコンピューターがネットワーク上にあり、そこにデータベースが配置されている場合、ネットワークの消費量も減ります。</span><span class="sxs-lookup"><span data-stu-id="470c3-111">Encoding workflow instance state information using the GZip reduces memory consumption in the SQL database and also reduces network consumption if the database resides on a different computer on the network from the computer on which the workflow service host is running.</span></span> <span data-ttu-id="470c3-112">一般的なガイダンスは、設定する、**インスタンス エンコーディング オプション**プロパティを**None**ワークフロー インスタンス状態が小さい場合。</span><span class="sxs-lookup"><span data-stu-id="470c3-112">A general guidance is to set the **Instance Encoding Option** property to **None** if the workflow instance state is small.</span></span>
