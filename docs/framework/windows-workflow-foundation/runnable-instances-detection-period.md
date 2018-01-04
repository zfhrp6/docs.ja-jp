---
title: "実行可能インスタンス検出期間"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 561ef96b6f043956822a1290d4a03a2e7411f6f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="runnable-instances-detection-period"></a>実行可能インスタンス検出期間
SQL Workflow Instance Store が実行する内部タスクは、定期的にアクティブになり、実行可能またはアクティブ化可能なインスタンスを永続性データベースで検出します。 **実行可能インスタンス検出期間**SQL Workflow Instance Store のプロパティを SQL Workflow Instance Store が実行可能またはアクティブ化可能なワークフローを検出する検出タスクを実行するまでの期間を指定します前回の検出サイクルの後に、永続性データベースでのインスタンス。  
  
 このプロパティの間隔を短く設定すると、ワークフロー インスタンスに関連付けられたタイマーの期限切れと、イベントのシグナリングおよび後続のインスタンスの読み込みの間の時間が短くなります。 ただし、ホストにかかる処理の負荷も増えるため、永続的なタイマーやホスト エラーがまれなシナリオでは望ましくない場合があります。 プロパティの型は TimeSpan で、プロパティの値は hh:mm:ss の形式です。 このプロパティの最小値は 00:00:01 です。 プロパティの既定値は 00:00:05 です。  
  
 詳細については検出とアクティブ化可能な実行可能なワークフロー インスタンスをアクティブ化を参照してください[インスタンスのアクティブ化](../../../docs/framework/windows-workflow-foundation/instance-activation.md)です。
