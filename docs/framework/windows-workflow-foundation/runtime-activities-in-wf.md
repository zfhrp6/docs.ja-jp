---
title: "WF のランタイム アクティビティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# WF のランタイム アクティビティ
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] には、永続化や終了などのワークフロー ランタイムの機能にアクセスするために、システムによって提供されるアクティビティがいくつか用意されています。  
  
|アクティビティ|説明|  
|-------------|--------|  
|<xref:System.Activities.Statements.Persist>|ワークフローがその状態を永続化するように明示的に要求します。|  
|<xref:System.Activities.Statements.TerminateWorkflow>|実行中のワークフロー インスタンスを終了します。|  
|<xref:System.Activities.Statements.NoPersistScope>|子アクティビティの永続化を防ぐコンテナー アクティビティ。|