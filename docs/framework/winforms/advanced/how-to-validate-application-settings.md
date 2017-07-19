---
title: "方法 : アプリケーション設定を検証する | Microsoft Docs"
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
  - "アプリケーション設定, 検証"
  - "アプリケーション設定, Windows フォーム"
  - "検証 (アプリケーション設定を)"
ms.assetid: 9f145ada-4267-436a-aa4c-c4dcffd0afb7
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : アプリケーション設定を検証する
ここでは、アプリケーション設定を永続化する前に検証する方法について説明します。  
  
 アプリケーションは厳密に型指定されるため、特定の設定に対してユーザーが誤った型を指定することはほとんどありません。  しかし、たとえば、誕生日として未来の日付を指定するなど、ユーザーが許容範囲外の設定値を割り当てようとすることもあります。  すべてのアプリケーション設定クラスの親クラスである <xref:System.Configuration.ApplicationSettingsBase> では、このような範囲チェックを有効にする 4 つのイベントが公開されています。  これらのイベントを処理すると、すべての検証コードを 1 か所に配置できるため、検証コードがプロジェクト全体に分散しません。  
  
 次の表で説明するように、使用するイベントは設定をいつ検証するかによって決まります。  
  
|Event|発生と使用|  
|-----------|-----------|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsLoaded>|設定プロパティ グループが初めて読み込まれた後に発生します。<br /><br /> このイベントを使用して、プロパティ グループ全体の初期値がアプリケーション内で使用される前に検証します。|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingChanging>|単一の設定プロパティの値が変更される前に発生します。<br /><br /> このイベントを使用して、単一のプロパティが変更される前に検証します。  処理および選択に関するフィードバックを即時にユーザーに提供できます。|  
|<xref:System.Configuration.ApplicationSettingsBase.PropertyChanged>|単一の設定プロパティの値が変更された後に発生します。<br /><br /> このイベントを使用して、単一のプロパティが変更された後で検証します。  時間がかかる非同期の検証プロセスが必要な場合を除き、このイベントを検証に使用することはほとんどありません。|  
|<xref:System.Configuration.ApplicationSettingsBase.SettingsSaving>|設定プロパティ グループが格納される前に発生します。<br /><br /> このイベントを使用して、プロパティ グループ全体の値がディスクに永続化される前に検証します。|  
  
 通常、同じアプリケーション内のすべてのイベントを検証の目的で使用することはありません。  たとえば、多くの場合、<xref:System.Configuration.ApplicationSettingsBase.SettingChanging> イベントを処理するだけですべての検証要件を満たすことができます。  
  
 一般に、イベント ハンドラーが無効な値を検出すると、次のいずれかを実行します。  
  
-   既定値など、正しいことが判明している値を自動的に入力します。  
  
-   情報のサーバー コードをユーザーに再照会します。  
  
-   関連付けられたアクションの前に発生した <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> や <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> などのイベントの場合は、引数 <xref:System.ComponentModel.CancelEventArgs> を使用して操作を取り消します。  
  
 イベント処理の詳細については、「[イベント ハンドラーの概要](../../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)」を参照してください。  
  
 次のプロシージャは、<xref:System.Configuration.ApplicationSettingsBase.SettingChanging> イベントまたは <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> イベントを使用して有効な誕生日をテストする方法を示しています。  このプロシージャは、アプリケーション設定を既に作成していることを前提にしています。この例では、 `DateOfBirth` という名前の設定の範囲チェックを実行します。  設定の作成の詳細については、「[方法 : アプリケーション設定を作成する](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)」を参照してください。  
  
### アプリケーション設定オブジェクトを取得するには  
  
-   次の項目のいずれかを実行してアプリケーション設定オブジェクト \(ラッパー インスタンス\) への参照を取得します。  
  
    -   Visual Studio の**プロパティ エディター**の \[アプリケーション設定\] ダイアログ ボックスを使用して設定を作成したときは、次の式によって使用している言語用に生成された既定の設定オブジェクトを取得できます。  
  
        ```csharp  
        Configuration.Settings.Default   
        ```  
  
        ```vb  
        MySettings.Default   
        ```  
  
         または  
  
    -   Visual Basic 開発者がプロジェクト デザイナーを使用してアプリケーション設定を作成したときは、[My.Settings オブジェクト](../../../../ocs/visual-basic/language-reference/objects/my-settings-object.md) を使用して設定を取得できます。  
  
         または  
  
    -   <xref:System.Configuration.ApplicationSettingsBase> から直接派生して設定を作成したときは、手動でクラスをインスタンス化する必要があります。  
  
        ```csharp  
        MyCustomSettings settings = new MyCustomSettings();  
        ```  
  
        ```vb  
        Dim Settings as New MyCustomSettings()  
        ```  
  
 次のプロシージャでは、この最後に紹介した項目を実行してアプリケーション設定オブジェクトを取得していることを前提にしています。  
  
### 設定の変更時にアプリケーション設定を検証するには  
  
1.  C\# を使用している場合は、フォームまたはコントロールの  `Load`  イベント内に <xref:System.Configuration.ApplicationSettingsBase.SettingChanging> イベントのイベント ハンドラーを追加します。  
  
     または  
  
     Visual Basic を使用している場合は、`WithEvents` キーワードを使用して `Settings` 変数を宣言します。  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        settings.SettingChanging += new SettingChangingEventHandler(MyCustomSettings_SettingChanging);  
    }  
    ```  
  
    ```vb  
    Public Sub Form1_Load(sender as Object, e as EventArgs)  
        AddHandler settings.SettingChanging, AddressOf MyCustomSettings_SettingChanging  
    End Sub   
    ```  
  
2.  イベント ハンドラーを定義し、その中に誕生日の範囲チェックを実行するコードを記述します。  
  
    ```csharp  
    private void MyCustomSettings_SettingChanging(Object sender, SettingChangingEventArgs e)  
    {  
        if (e.SettingName.Equals("DateOfBirth")) {  
            Date newDate = (Date)e.NewValue;  
            If (newDate > Date.Now) {  
                e.Cancel = true;  
                // Inform the user.  
            }  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub MyCustomSettings_SettingChanging(sender as Object, e as SettingChangingEventArgs) Handles Settings.SettingChanging  
        If (e.SettingName.Equals("DateOfBirth")) Then  
            Dim NewDate as Date = CType(e.NewValue, Date)  
            If (NewDate > Date.Now) Then  
                e.Cancel = True  
                ' Inform the user.  
            End If  
        End If  
    End Sub  
    ```  
  
### 保存時にアプリケーション設定を検証するには  
  
1.  フォームまたはコントロールの  `Load`  イベント内に <xref:System.Configuration.ApplicationSettingsBase.SettingsSaving> イベントのイベント ハンドラーを追加します。  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)   
    {  
        settings.SettingsSaving += new SettingsSavingEventHandler(MyCustomSettings_SettingsSaving);  
    }  
    ```  
  
    ```vb  
    Public Sub Form1_Load(Sender as Object, e as EventArgs)  
        AddHandler settings.SettingsSaving, AddressOf MyCustomSettings_SettingsSaving  
    End Sub  
    ```  
  
2.  イベント ハンドラーを定義し、その中に誕生日の範囲チェックを実行するコードを記述します。  
  
    ```csharp  
    private void MyCustomSettings_SettingsSaving(Object sender, SettingsSavingEventArgs e)  
    {  
        if (this["DateOfBirth"] > Date.Now) {  
            e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Private Sub MyCustomSettings_SettingsSaving(Sender as Object, e as SettingsSavingEventArgs)  
        If (Me["DateOfBirth"] > Date.Now) Then  
            e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## 参照  
 [Windows フォーム内でのイベント ハンドラーの作成](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)   
 [方法 : アプリケーション設定を作成する](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md)