---
title: カスタム アクティビティの設計と実装
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4e30e63d-6e33-4842-a7a4-ce807cef1fad
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bafa54764ba8b02dd05cadd65c3f3cbc64c4b081
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="designing-and-implementing-custom-activities"></a>カスタム アクティビティの設計と実装
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] のカスタム アクティビティを作成するには、システム標準アクティビティを複合アクティビティにアセンブルするか、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity>、または <xref:System.Activities.NativeActivity> から派生する新しい型を作成します。 ここでは、いずれかのメソッドを使用してカスタム アクティビティを作成する方法について説明します。  
  
> [!IMPORTANT]
>  既定では、カスタム アクティビティは、ワークフロー デザイナー内で、アクティビティ名を含む単純な四角形として表示されます。 ワーク フロー デザイナーでアクティビティのカスタム ビジュアル表現を指定するには、カスタム デザイナーを作成する必要があります。 詳細については、次を参照してください。[を使用してカスタム アクティビティ デザイナーおよびテンプレート](../../../docs/framework/windows-workflow-foundation/using-custom-activity-designers-and-templates.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [アクティビティ作成オプション](../../../docs/framework/windows-workflow-foundation/activity-authoring-options-in-wf.md)  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] で使用できる作成スタイルについて説明します。  
  
 [カスタム アクティビティの使用](../../../docs/framework/windows-workflow-foundation/using-a-custom-activity.md)  
 ワークフロー プロジェクトにカスタム アクティビティを追加する方法について説明します。  
  
  [非同期アクティビティの作成](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md)  
 非同期アクティビティを作成する方法について説明します。  
  
 [アクティビティ検証の構成](../../../docs/framework/windows-workflow-foundation/configuring-activity-validation.md)  
 アクティビティの検証を使用して、アクティビティを実行する前にその構成エラーを特定および報告する方法について説明します。  
  
 [実行時におけるアクティビティの作成](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md)  
 <xref:System.Activities.DynamicActivity> を使用して実行時にアクティビティを作成する方法について説明します。  
  
 [ワークフロー実行プロパティ](../../../docs/framework/windows-workflow-foundation/workflow-execution-properties.md)  
 ワークフロー実行プロパティを使用して、アクティビティの環境にコンテキスト固有のプロパティを追加する方法について説明します。  
  
 [アクティビティ デリゲートの使用](../../../docs/framework/windows-workflow-foundation/using-activity-delegates.md)  
 アクティビティ デリゲートを含むアクティビティを作成および使用する方法について説明します。  
  
 [アクティビティのローカライズ](../../../docs/framework/windows-workflow-foundation/activity-localization.md)  
 アクティビティの文字列リソースのローカライズを使用する方法について説明します。  
  
 [アクティビティ拡張機能の使用](../../../docs/framework/windows-workflow-foundation/using-activity-extensions.md)  
 アクティビティ拡張機能を作成および使用する方法について説明します。  
  
 [ワークフローからの OData フィードの利用](../../../docs/framework/windows-workflow-foundation/consuming-odata-feeds-from-a-workflow.md)  
 ワークフローから WCF Data Service を呼び出すためのいくつかの方法について説明します。  
  
 [アクティビティ定義のスコープ設定と表示](../../../docs/framework/windows-workflow-foundation/activity-definition-scoping-and-visibility.md)  
 アクティビティのデータのスコープとメンバーの参照範囲を定義するためのオプションおよび規則について説明します。
