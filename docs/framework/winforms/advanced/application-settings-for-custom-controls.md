---
title: "カスタム コントロールのアプリケーション設定 | Microsoft Docs"
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
  - "アプリケーション設定 [Windows フォーム], カスタム コントロール"
  - "カスタム コントロール [Windows フォーム], アプリケーション設定"
ms.assetid: f44afb74-76cc-44f2-890a-44b7cdc211a1
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# カスタム コントロールのアプリケーション設定
コントロールがサードパーティのアプリケーションでホストされている場合、アプリケーション設定を永続化するための機能をカスタム コントロールに持たせるには特定のタスクを完了する必要があります。  
  
 アプリケーション設定機能に関するほとんどのドキュメントは、スタンドアロン アプリケーションを作成していることを前提にしています。  ただし、他の開発者が作成したアプリケーション内でホストされるコントロールを作成する場合には、コントロールが設定を適切に永続化できるように、追加の手順を実行する必要があります。  
  
## アプリケーション設定とカスタム コントロール  
 コントロールで設定を適切に永続化できるようにするためには、<xref:System.Configuration.ApplicationSettingsBase> から派生した独自の専用アプリケーション設定ラッパー クラスを作成することによってプロセスをカプセル化する必要があります。  また、メイン コントロール クラスで <xref:System.Configuration.IPersistComponentSettings> を実装する必要があります。  このインターフェイスには、複数のプロパティと 2 つのメソッド \(<xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> および <xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A>\) が含まれます。  Visual Studio の **Windows フォーム デザイナー**を使用してコントロールをフォームに追加する場合、コントロールの初期化時に、Windows フォームは自動的に <xref:System.Configuration.IPersistComponentSettings.LoadComponentSettings%2A> を呼び出します。<xref:System.Configuration.IPersistComponentSettings.SaveComponentSettings%2A> は、コントロールの  `Dispose`  メソッド内で独自に呼び出す必要があります。  
  
 また、カスタム コントロールのアプリケーション設定が Visual Studio などデザイン時の環境で正しく動作するように、次を実装する必要があります。  
  
1.  <xref:System.ComponentModel.IComponent> を 1 つのパラメーターとして使用するコンストラクターを含む、カスタム アプリケーション設定クラス。  このクラスを使用して、すべてのアプリケーション設定を読み込みます。  このクラスの新しいインスタンスを作成するときに、コンストラクターを使用してカスタム コントロールを渡します。  
  
2.  コントロールを作成し、フォームの <xref:System.Windows.Forms.Form.Load> イベント ハンドラーなどに配置した後に、カスタム設定クラスを作成します。  
  
 カスタム設定クラスを作成する手順については、「[方法 : アプリケーション設定を作成する](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)」を参照してください。  
  
## 設定キーと共有設定  
 コントロールの中には、同じフォーム内で何度も使用できるものがあります。  ほとんどの場合、このようなコントロールが個々の設定を独自に永続化するように設定すると便利です。  <xref:System.Configuration.IPersistComponentSettings> の <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> プロパティを使用すると、フォーム上のコントロールの複数のバージョンを区別する一意の文字列を指定できます。  
  
 <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> を実装する最も簡単な方法は、コントロールの <xref:System.Windows.Forms.Control.Name%2A> プロパティを <xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> に使用することです。  コントロールの設定を読み込むときまたは保存するときに、<xref:System.Configuration.IPersistComponentSettings.SettingsKey%2A> の値を <xref:System.Configuration.ApplicationSettingsBase> クラスの <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> プロパティに渡します。  アプリケーション設定は、ユーザーの設定を XML ファイルに永続化するときにこの一意キーを使用します。   `Text`  プロパティの設定を保存する  `CustomControl1`  という名前のカスタム コントロールのインスタンスを  `<userSettings>`  セクションが検索するしくみを次のコード例に示します。  
  
```  
<userSettings>  
    <CustomControl1>  
        <setting name="Text" serializedAs="string">  
            <value>Hello, World</value>  
        </setting>  
    </CustomControl1>  
</userSettings>  
```  
  
 <xref:System.Configuration.ApplicationSettingsBase.SettingsKey%2A> の値を指定しないコントロールのすべてのインスタンスは、同じ設定を共有します。  
  
## 参照  
 <xref:System.Configuration.ApplicationSettingsBase>   
 <xref:System.Configuration.IPersistComponentSettings>   
 [アプリケーション設定アーキテクチャ](../../../../docs/framework/winforms/advanced/application-settings-architecture.md)