---
title: "アプリケーション設定の属性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "アプリケーション設定 [Windows フォーム], 属性"
  - "属性 [Windows フォーム], アプリケーション設定"
  - "ラッパー クラス, アプリケーション設定"
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# アプリケーション設定の属性
アプリケーション設定アーキテクチャには、アプリケーション設定ラッパー クラスまたはその個々のプロパティに適用できるさまざまな属性が用意されています。  これらの属性は、カスタム ラッパーの指定要件に合わせて機能を調節できるように、アプリケーション設定インフラストラクチャ \(多くの場合、具体的には設定プロバイダー\) によって実行時にチェックされます。  
  
 アプリケーション設定ラッパー クラス、このクラスの個々のプロパティ、またはその両方に適用できる属性を次の表に示します。  定義上、各設定プロパティに 1 つのスコープ属性 \(**UserScopedSettingAttribute** または **ApplicationScopedSettingAttribute**\) だけを適用する必要があります。  
  
> [!NOTE]
>  <xref:System.Configuration.SettingsProvider> クラスから派生するカスタム設定プロバイダーは、**ApplicationScopedSettingAttribute**、**UserScopedSettingAttribute**、**DefaultSettingValueAttribute** の 3 つの属性だけを認識する必要があります。  
  
|属性|Target|Description|  
|--------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|Both|永続化に使用される設定プロバイダーの短い名前を指定します。<br /><br /> この属性を指定しないときは、既定のプロバイダー <xref:System.Configuration.LocalFileSettingsProvider> を指定したものと見なされます。|  
|<xref:System.Configuration.UserScopedSettingAttribute>|Both|ユーザー スコープのアプリケーション設定としてプロパティを定義します。|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|Both|アプリケーション スコープのアプリケーション設定としてプロパティを定義します。|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|プロパティ|プロバイダーによって、このプロパティのハードコーディングされた既定値に逆シリアル化できる文字列を指定します。<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider> はこの属性を必要としません。既に永続化されている値がある場合は、この属性で指定された値をオーバーライドします。|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|プロパティ|主に実行時ツールとデザイン時ツールによって使用される、個々の設定の記述テストを指定します。|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|Class|設定グループの名前を明示的に指定します。  この属性を指定しない場合、<xref:System.Configuration.ApplicationSettingsBase> はラッパー クラス名を使用します。|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|Class|主に実行時ツールとデザイン時ツールによって使用される、設定グループの記述テストを指定します。|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|Both|設定グループまたはプロパティに提供する必要がある 0 個以上の管理機能サービスを指定します。  使用できるサービスは、<xref:System.Configuration.SettingsManageability> 列挙型によって記述されます。|  
|<xref:System.Configuration.SpecialSettingAttribute>|プロパティ|設定プロバイダーによる特別な処理を意味する特別な定義済みカテゴリ \(接続文字列など\) に設定が属することを示します。  この属性の定義済みカテゴリは、<xref:System.Configuration.SpecialSetting> 列挙型によって定義されます。|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|Both|設定グループまたはプロパティに推奨されるシリアル化機構を指定します。  使用できるシリアル化機構は、<xref:System.Configuration.SettingsSerializeAs> 列挙型によって定義されます。|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|プロパティ|マークしたプロパティのアプリケーション アップグレード機能を設定プロバイダーがすべて無効にすることを指定します。|  
  
 *クラス*は、その属性をアプリケーション設定ラッパー クラスだけに適用できることを示します。  *プロパティ*は、その属性を設定プロパティだけに適用できることを示します。  *両方*は、その属性をどちらのレベルでも適用できることを示します。  
  
## 参照  
 <xref:System.Configuration.ApplicationSettingsBase>   
 <xref:System.Configuration.SettingsProvider>   
 [アプリケーション設定アーキテクチャ](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)   
 [How to: Create Application Settings](http://msdn.microsoft.com/ja-jp/53b3af80-1c02-4e35-99c6-787663148945)