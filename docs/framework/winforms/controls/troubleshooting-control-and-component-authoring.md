---
title: "コントロールとコンポーネントの作成時のトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "コンポーネント [Windows フォーム], トラブルシューティング"
  - "コントロール [Windows フォーム], トラブルシューティング"
  - "トラブルシューティング (コンポーネントの)"
  - "トラブルシューティング (コントロール)"
  - "Windows フォーム コントロール, デバッグ"
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# コントロールとコンポーネントの作成時のトラブルシューティング
このトピックでは、コンポーネントとコントロールの作成時に発生する次の一般的な問題について説明します。  詳細については、「[コンポーネントによるプログラミング](../Topic/Programming%20with%20Components.md)」を参照してください。  
  
-   ツールボックスにコントロールを追加できない  
  
-   Windows フォームのユーザー コントロールまたはコンポーネントをデバッグできない  
  
-   継承されたコントロールまたはコンポーネントでイベントが 2 回発生する  
  
-   デザイン時エラー : "コンポーネント '*コンポーネント名*' を生成できませんでした。"  
  
-   STAThreadAttribute  
  
-   コンポーネント アイコンがツールボックスに表示されない  
  
## ツールボックスにコントロールを追加できない  
 別のプロジェクトで作成したカスタム コントロールまたはサードパーティ コントロールを**ツールボックス**に追加する場合は、手動で追加する必要があります。  コントロールまたはコンポーネントが現在のプロジェクトに含まれているときは、**ツールボックス**に自動的に表示されます。  詳細については、「[チュートリアル : ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)」を参照してください。  
  
#### コントロールをツールボックスに追加するには  
  
1.  **\[ツールボックス\]** を右クリックして、ショートカット メニューの **\[アイテムの選択\]** をクリックします。  
  
2.  **\[ツールボックス アイテムの選択\]** ダイアログ ボックスで、コンポーネントを追加します。  
  
    -   .NET Framework コンポーネントまたはコントロールを追加するには、**\[.NET Framework コンポーネント\]** タブをクリックします。  
  
         または  
  
    -   COM コンポーネントまたは ActiveX コントロールを追加するには、**\[COM コンポーネント\]** タブをクリックします。  
  
3.  ダイアログ ボックスにコントロールが一覧表示されたら、コントロールが選択されていることを確認して **\[OK\]** をクリックします。  
  
     コントロールが**ツールボックス**に追加されます。  
  
4.  ダイアログ ボックスにコントロールが一覧表示されない場合は、次の手順を実行します。  
  
    1.  **\[Browse\]** をクリックします。  
  
    2.  コントロールが入っている .dll ファイルが格納されたフォルダーを参照します。  
  
    3.  .dll ファイルを選択し、**\[開く\]** をクリックします。  
  
         ダイアログ ボックスにコントロールが表示されます。  
  
    4.  コントロールが選択されていることを確認して **\[OK\]** をクリックします。  
  
         コントロールが**ツールボックス**に追加されます。  
  
## Windows フォームのユーザー コントロールまたはコンポーネントをデバッグできない  
 コントロールが <xref:System.Windows.Forms.UserControl> クラスから派生している場合は、テスト コンテナーで実行時の動作をデバッグできます。  詳細については、「[方法 : UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。  
  
 その他のカスタム コントロールやカスタム コンポーネントはスタンドアロン プロジェクトではありません。  そのため、Windows フォーム プロジェクトなどのアプリケーションでホストする必要があります。  コントロールまたはコンポーネントをデバッグするには、Windows フォーム プロジェクトに追加する必要があります。  
  
#### コントロールまたはコンポーネントをデバッグするには  
  
1.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックしてソリューションをビルドします。  
  
2.  **\[ファイル\]** メニューで、**\[追加\]**、**\[新しいプロジェクト\]** の順にクリックして、アプリケーションにテスト プロジェクトを追加します。  
  
3.  **\[新しいプロジェクトの追加\]** ダイアログ ボックスで、プロジェクトの種類として **\[Windows アプリケーション\]** を選択します。  
  
4.  **ソリューション エクスプローラー**で、新しいプロジェクトの **\[参照設定\]** ノードを右クリックします。  ショートカット メニューの **\[参照の追加\]** をクリックして、コントロールまたはコンポーネントを含むプロジェクトへの参照を追加します。  
  
5.  コントロールまたはコンポーネントのインスタンスをテスト プロジェクトに作成します。  コンポーネントが**ツールボックス**に表示されている場合は、デザイナー画面にドラッグできます。または、次のコード例に示すように、プログラムによってインスタンスを作成できます。  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     これで、コントロールまたはコンポーネントを通常の方法でデバッグできるようになります。  
  
 デバッグの詳細については、「[Visual Studio でのデバッグ](../Topic/Debugging%20in%20Visual%20Studio.md)」および「[チュートリアル : カスタム Windows フォーム コントロールのデザイン時のデバッグ](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)」を参照してください。  
  
## 継承されたコントロールまたはコンポーネントでイベントが 2 回発生する  
 `Handles` 句が重複していることが原因と考えられます。  詳細については、「[Troubleshooting Inherited Event Handlers in Visual Basic](../Topic/Troubleshooting%20Inherited%20Event%20Handlers%20in%20Visual%20Basic.md)」を参照してください。  
  
## デザイン時エラー : "コンポーネント 'コンポーネント名' を生成できませんでした。"  
 コンポーネントやコントロールは、パラメーターなしの既定のコンストラクターを提供する必要があります。  デザイン環境は、コンポーネントやコントロールのインスタンスを作成するときに、パラメーターを受け取るコンストラクター オーバーロードにパラメーターを提供しません。  
  
## STAThreadAttribute  
 <xref:System.STAThreadAttribute> は、Windows フォームがシングルスレッド アパートメント モデルを使用することを共通言語ランタイム \(CLR: Common Language Runtime\) に通知します。  この属性を Windows フォーム アプリケーションの `Main` メソッドに適用していない場合、意図しない動作が発生する場合があります。  たとえば、<xref:System.Windows.Forms.ListView> などのコントロールに背景イメージが表示されない場合があります。  また、一部のコントロールでオートコンプリート動作やドラッグ アンド ドロップ動作を正常に行うためには、この属性が必要になる場合があります。  
  
## コンポーネント アイコンがツールボックスに表示されない  
 <xref:System.Drawing.ToolboxBitmapAttribute> を使用してアイコンをカスタム コンポーネントに関連付けた場合、自動的に生成されたコンポーネントのビットマップがツールボックスに表示されません。  ビットマップを表示するには、**\[ツールボックス アイテムの選択\]** ダイアログ ボックスを使用してコントロールを再読み込みします。  詳細については、「[方法 : コントロールにツールボックス ビットマップを指定する](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)」を参照してください。  
  
## 参照  
 [デザイン時の Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)   
 [チュートリアル : ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)   
 [方法 : UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)   
 [チュートリアル : カスタム Windows フォーム コントロールのデザイン時のデバッグ](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)   
 [コンポーネントの作成](../Topic/Component%20Authoring.md)   
 [Troubleshooting Design\-Time Development](../Topic/Troubleshooting%20Design-Time%20Development.md)   
 [コンポーネントによるプログラミング](../Topic/Programming%20with%20Components.md)