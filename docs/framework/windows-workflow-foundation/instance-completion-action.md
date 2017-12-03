---
title: "インスタンス完了アクション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 90cc99d2-9fef-42fd-bcbf-a56917993721
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 83dec7ef4c911c0bca94caf7cc4c4bf832c8e1b6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="instance-completion-action"></a>インスタンス完了アクション
**インスタンス完了アクション**SQL Workflow Instance Store のプロパティかどうか、データやワークフロー インスタンスのメタデータが削除された永続性データベースからのインスタンスが完了した後を指定できます。 このプロパティの値を指定できます**DeleteAll**と**DeleteNothing**です。 これらのオプションについて次の一覧で説明します。  
  
-   **DeleteAll (既定値)。** このプロパティの値を DeleteAll に設定すると、ワークフロー インスタンスの完了後に、永続性データベースからワークフロー インスタンスのデータおよびメタデータは削除されます。  
  
-   **DeleteNothing です。** このプロパティの値を DeleteNothing に設定すると、ワークフロー インスタンスが完了しても、ワークフロー インスタンスのデータおよびメタデータは永続性データベースに残ります。  
  
    > [!CAUTION]
    >  インスタンスの完了後にインスタンス状態情報を残すと、永続性データベースのサイズが大きくなります。 データベースのサイズが大きくなるにつれて、永続性サブシステムが実行するデータベース操作にかかる時間が長くなります。そのため、永続性データベースからインスタンス状態情報を定期的に削除して、パフォーマンスの要件を満たすレベルでサービスが実行されるようにします。
