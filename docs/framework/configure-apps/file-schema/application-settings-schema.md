---
title: "アプリケーション設定のスキーマ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "アプリケーション設定, スキーマ [Windows フォーム]"
  - "構成スキーマ [.NET Framework], アプリケーション設定"
  - "スキーマ (アプリケーション設定)"
  - "Windows フォーム, アプリケーション設定スキーマ"
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
caps.latest.revision: 3
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 3
---
# アプリケーション設定のスキーマ
アプリケーション設定によって、Windows フォームまたは ASP.NET アプリケーションはアプリケーション スコープおよびユーザー スコープの設定を格納および取得できます。  ここにおける「設定」は、データベース接続文字列からユーザーの既定のウィンドウ サイズにいたるまでのアプリケーションまたは現在のユーザー固有の情報を意味します。  
  
 既定では、Windows フォーム アプリケーションのアプリケーション設定は、.NET 構成システムを使用して設定を XML 構成ファイルに格納する <xref:System.Configuration.LocalFileSettingsProvider> を使用します。  アプリケーション設定が使用するファイルの詳細については、「[アプリケーション設定アーキテクチャ](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)」を参照してください。  
  
 アプリケーション設定は、使用する構成ファイルで次の要素を定義します。  
  
|要素|説明|  
|--------|--------|  
|`<applicationSettings>` 要素|アプリケーション固有のすべての `<setting>` タグが含まれます。|  
|`<userSettings>` 要素|現在のユーザー固有のすべての `<setting>` タグが含まれます。|  
|`<setting>` 要素|設定を定義します。  `<applicationSettings>` または `<userSettings>` の子要素です。|  
|`<value>` 要素|設定の値を定義します。  `<setting>` の子要素です。|  
  
## \<applicationSettings\> 要素  
 この要素には \<、クライアント コンピューターのアプリケーションのインスタンス固有のすべての構成\> タグが含まれます。  属性は定義されません。  
  
## \<userSettings\> 要素  
 この要素は \<\>、アプリケーションを使用しているユーザー固有のすべての構成 タグが含まれます。  属性は定義されません。  
  
## \<構成\> 要素  
 この要素は、設定を定義します。  次の属性を持ちます。  
  
|要素|説明|  
|--------|--------|  
|`name`|必須。  設定の一意の ID です。  Visual Studio を使用して作成された設定は `ProjectName``.Properties.Settings` という名前で保存されます。|  
|`serializedAs`|必須。  テキストに値をシリアル化するために使用する形式です。  次の値を指定できます。<br /><br /> -   `string`:   値は、<xref:System.ComponentModel.TypeConverter> を使用して文字列としてシリアル化されます。<br />-   `xml`.  値は、XML シリアル化を使用してシリアル化されます。<br />-   `binary`:   値は、バイナリ シリアル化を使用してテキストでエンコードされたバイナリとしてシリアル化されます。<br />-   `custom`:   設定プロバイダーは、この設定に固有の情報を保有してシリアル化および逆シリアル化を実行します。<br />-   バイナリまたはカスタムのシリアル化を使用する場合は、独自に設定クラスを定義し、<xref:System.Configuration.SettingsSerializeAsAttribute> を使用してバイナリまたはカスタムのシリアル化を指定する必要があります。|  
  
## \<値要素\>  
 この要素には、設定の値が含まれます。  
  
## 使用例  
 2 つのアプリケーション スコープの設定および 2 つのユーザー スコープの設定を定義するアプリケーション設定ファイルのコード例を次に示します。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </sectionGroup>  
        <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />  
        </sectionGroup>  
    </configSections>  
    <applicationSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="Cursor" serializeAs="String">  
                <value>Default</value>  
            </setting>  
            <setting name="DoubleBuffering" serializeAs="String">  
                <value>False</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </applicationSettings>  
    <userSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="FormTitle" serializeAs="String">  
                <value>Form1</value>  
            </setting>  
            <setting name="FormSize" serializeAs="String">  
                <value>595, 536</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </userSettings>  
</configuration>  
```  
  
## 参照  
 [アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)   
 [アプリケーション設定アーキテクチャ](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)