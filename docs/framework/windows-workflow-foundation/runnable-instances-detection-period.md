---
title: "実行可能インスタンス検出期間 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ea5c787-b638-47fd-bfc8-ede8c2898ce6
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 実行可能インスタンス検出期間
SQL Workflow Instance Store が実行する内部タスクは、定期的にアクティブになり、実行可能またはアクティブ化可能なインスタンスを永続性データベースで検出します。SQL Workflow Instance Store の**実行可能インスタンス検出期間**プロパティは、前の検出サイクルの後、SQL Workflow Instance Store が実行可能またはアクティブ化可能なワークフロー インスタンスを永続性データベースで検出するために検出タスクを実行するまでの期間を指定します。  
  
 このプロパティの間隔を短く設定すると、ワークフロー インスタンスに関連付けられたタイマーの期限切れと、イベントのシグナリングおよび後続のインスタンスの読み込みの間の時間が短くなります。ただし、ホストにかかる処理の負荷も増えるため、永続的なタイマーやホスト エラーがまれなシナリオでは望ましくない場合があります。プロパティの型は TimeSpan で、プロパティの値は hh:mm:ss の形式です。このプロパティの最小値は 00:00:01 です。プロパティの既定値は 00:00:05 です。  
  
 実行可能およびアクティブ化可能なワークフロー インスタンスを検出およびアクティブ化する方法の詳細については、「[インスタンスのアクティブ化処理](../../../docs/framework/windows-workflow-foundation//instance-activation.md)」を参照してください。