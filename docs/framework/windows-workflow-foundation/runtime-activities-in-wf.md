---
title: WF のランタイム アクティビティ
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: 7981d3f75c8fd2d0ddd2ae0233f425c2907c270c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513036"
---
# <a name="runtime-activities-in-wf"></a>WF のランタイム アクティビティ
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] には、永続化や終了などのワークフロー ランタイムの機能にアクセスするために、システムによって提供されるアクティビティがいくつか用意されています。  
  
|アクティビティ|説明|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|ワークフローがその状態を永続化するように明示的に要求します。|  
|<xref:System.Activities.Statements.TerminateWorkflow>|実行中のワークフロー インスタンスを終了します。|  
|<xref:System.Activities.Statements.NoPersistScope>|子アクティビティの永続化を防ぐコンテナー アクティビティ。|
