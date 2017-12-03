---
title: "セキュリティ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0063497bc500a11d59dd88e0cb7d738d5c4bb6e5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="security"></a>セキュリティ
SQL Workflow Instance Store は、次のデータベース セキュリティ ロールを使用して、永続性データベースのインスタンス状態情報へのアクセスをセキュリティ保護します。  
  
-   **System.Activities.DurableInstancing.InstanceStoreUsers**です。 このロールには、パブリック ビューへの読み取りおよび書き込みのアクセス権と、インスタンスの作成、読み込み、保存に関連するストアド プロシージャへの実行権限があります。  
  
-   **System.Activities.DurableInstancing.InstanceStoreObservers**です。 このロールには、パブリック ビューへの読み取り専用アクセス権があります。  
  
-   **System.Activities.DurableInstancing.WorkflowActivationUsers**です。 このロールには、インスタンスのアクティベーション プロセスにかかわるストアド プロシージャへの実行権限があります。 インスタンスのアクティブ化の詳細については、次を参照してください。[インスタンスのアクティブ化](../../../docs/framework/windows-workflow-foundation/instance-activation.md)です。 汎用ホスト ([!INCLUDE[dublin](../../../includes/dublin-md.md)] のワークフロー管理サービスなど) を実行するユーザー アカウントは、このデータベース ロールに追加する必要があります。  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Windows Server App Fabric で永続化ストアのセキュリティを参照してください[App Fabric で永続的ストアに対するセキュリティの構成](http://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  インスタンス ストア内にある固有のインスタンス データへのアクセス権を持つクライアントは、同じインスタンス ストア内にあるその他すべてのインスタンスにもアクセスできます。 インスタンス ストアでは、インスタンス レベルでセキュリティ アクセス許可を指定することはできません。 個別のインスタンス ストアを作成し、ストアごとに、各グループやユーザーのアクセス権を設定します。
