---
title: "アプリケーション設定の属性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b2ed0a0393f505d0126508e574b1cd9abe138866
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="application-settings-attributes"></a>アプリケーション設定の属性
アプリケーション設定アーキテクチャでは、アプリケーション設定のラッパー クラスまたはその個々 のプロパティに適用できる多くの属性を提供します。 これらの属性は、実行時に示されたカスタム ラッパーのニーズにその動作を調整するためにアプリケーション設定のインフラストラクチャ、具体的には多くの場合、設定プロバイダーをでチェックします。  
  
 次の表は、アプリケーション設定のラッパー クラス、このクラスの個々 のプロパティ、またはその両方に適用できる属性を一覧表示します。 定義上、スコープを 1 つの属性のみ —**UserScopedSettingAttribute**または**ApplicationScopedSettingAttribute**— 各設定のプロパティに適用する必要があります。  
  
> [!NOTE]
>  派生したカスタム設定プロバイダー、<xref:System.Configuration.SettingsProvider>クラス、次の 3 つの属性を認識するために必要なだけ: **ApplicationScopedSettingAttribute**、 **UserScopedSettingAttribute**、および**DefaultSettingValueAttribute**です。  
  
|属性|ターゲット|説明|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|両方|永続化に使用する設定プロバイダーの短い名前を指定します。<br /><br /> この属性が指定されていない場合、既定のプロバイダー<xref:System.Configuration.LocalFileSettingsProvider>と見なされます。|  
|<xref:System.Configuration.UserScopedSettingAttribute>|両方|アプリケーションのユーザー スコープ設定とプロパティを定義します。|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|両方|アプリケーションのアプリケーション スコープ設定として、プロパティを定義します。|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|プロパティ|このプロパティの既定のハードコード値に、プロバイダーによって逆シリアル化できる文字列を指定します。<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider>この属性は必要ありません、この属性である場合、値既に永続化の指定には、任意の値をよりも優先されます。|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|プロパティ|実行時およびデザイン時ツールで、主に使用される、個々 の設定のテストの説明を提供します。|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|クラス|設定グループの明示的な名前を提供します。 この属性が見つからない場合<xref:System.Configuration.ApplicationSettingsBase>ラッパー クラス名を使用します。|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|クラス|設定グループで、実行時およびデザイン時ツールで、主に使用されるテストの説明を提供します。|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|両方|設定グループまたはプロパティに指定する必要がある、0 個以上の管理の容易性サービスを指定します。 使用可能なサービスが記載されている、<xref:System.Configuration.SettingsManageability>列挙します。|  
|<xref:System.Configuration.SpecialSettingAttribute>|プロパティ|設定が設定プロバイダーによる特別な処理を提案する接続文字列など、特別な定義済みのカテゴリに属することを示します。 この属性の定義済みのカテゴリがによって定義されている、<xref:System.Configuration.SpecialSetting>列挙します。|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|両方|設定グループまたはプロパティの推奨されるシリアル化機構を指定します。 使用可能なシリアル化メカニズムが定義されている、<xref:System.Configuration.SettingsSerializeAs>列挙します。|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|プロパティ|設定プロバイダーにマークされたプロパティのすべてのアプリケーションのアップグレードの機能が無効にする必要がありますを指定します。|  
  
 *クラス*アプリケーション設定のラッパー クラスにのみ、属性を適用できることを示します。 *プロパティ*属性が設定プロパティだけに適用できることを示します。 *両方*いずれかのレベルで属性を適用できることを示します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 [アプリケーション設定アーキテクチャ](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)  
 [方法: アプリケーション設定を作成する](http://msdn.microsoft.com/library/53b3af80-1c02-4e35-99c6-787663148945)
