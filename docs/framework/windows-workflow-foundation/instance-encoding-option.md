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
ms.openlocfilehash: a874f88b787a99af0461ff47c3ae246442af2f19
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="instance-encoding-option"></a>インスタンス エンコーディング オプション
**インスタンス エンコーディング オプション**SQL Workflow Instance Store のプロパティを使用して、SQL 永続化プロバイダーが保存する前に GZip アルゴリズムを使用して、ワークフロー インスタンス状態情報を圧縮するかどうかを指定できます、永続性データベースに情報です。 このプロパティに使用できる値は GZip と None です。 既定値は None です。 これらのオプションを次の一覧で説明します。  
  
1.  **GZip**です。 永続化プロバイダーは、永続性データベースに状態情報を永続化する前に、GZip アルゴリズムを使用して状態情報をエンコードします。  
  
2.  **None**です。 永続化プロバイダーは、永続性データベースに情報を保存する前は、状態情報をエンコードしません。  
  
 GZip を使用してワークフロー インスタンスの状態情報をエンコードすると、SQL データベースのメモリ消費量が減ります。また、ワークフロー サービス ホストが実行されているコンピューターとは異なるコンピューターがネットワーク上にあり、そこにデータベースが配置されている場合、ネットワークの消費量も減ります。 一般的なガイダンスは、設定する、**インスタンス エンコーディング オプション**プロパティを**None**ワークフロー インスタンス状態が小さい場合。
