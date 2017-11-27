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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a17b77293d9a12fd3720fc54cb6c17a28a8c6ed0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="security"></a>セキュリティ
SQL Workflow Instance Store は、次のデータベース セキュリティ ロールを使用して、永続性データベースのインスタンス状態情報へのアクセスをセキュリティ保護します。  
  
-   **System.Activities.DurableInstancing.InstanceStoreUsers**です。 このロールには、パブリック ビューへの読み取りおよび書き込みのアクセス権と、インスタンスの作成、読み込み、保存に関連するストアド プロシージャへの実行権限があります。  
  
-   **System.Activities.DurableInstancing.InstanceStoreObservers**です。 このロールには、パブリック ビューへの読み取り専用アクセス権があります。  
  
-   **System.Activities.DurableInstancing.WorkflowActivationUsers**です。 このロールには、インスタンスのアクティベーション プロセスにかかわるストアド プロシージャへの実行権限があります。 インスタンスのアクティブ化の詳細については、次を参照してください。[インスタンスのアクティブ化](../../../docs/framework/windows-workflow-foundation/instance-activation.md)です。 汎用ホスト ([!INCLUDE[dublin](../../../includes/dublin-md.md)] のワークフロー管理サービスなど) を実行するユーザー アカウントは、このデータベース ロールに追加する必要があります。  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Windows Server App Fabric で永続化ストアのセキュリティを参照してください[App Fabric で永続的ストアに対するセキュリティの構成](http://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  インスタンス ストア内にある固有のインスタンス データへのアクセス権を持つクライアントは、同じインスタンス ストア内にあるその他すべてのインスタンスにもアクセスできます。 インスタンス ストアでは、インスタンス レベルでセキュリティ アクセス許可を指定することはできません。 個別のインスタンス ストアを作成し、ストアごとに、各グループやユーザーのアクセス権を設定します。
