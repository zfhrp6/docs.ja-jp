---
title: "方法 : 複合コントロールを作成する | Microsoft Docs"
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
  - "複合コントロール, 作成"
  - "ユーザー コントロール [Windows フォーム], 作成"
  - "ユーザー コントロール [Windows フォーム], 継承"
  - "UserControl クラス, 作成 (複合コントロールを)"
ms.assetid: 79c9cf05-5ab6-4a18-886d-88a64748b098
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : 複合コントロールを作成する
複合コントロールはさまざまな方法で使用できます。  Windows デスクトップ アプリケーション プロジェクトの一部として作成し、そのプロジェクトのフォームでだけ使用することもできます。  また、Windows コントロール ライブラリ プロジェクトで作成し、プロジェクトをアセンブリにコンパイルして、コントロールを他のプロジェクトで使用することもできます。  さらに、そのコントロールから継承し、ビジュアル継承を使用して、特定の用途に合わせて簡単にカスタマイズすることもできます。  
  
> [!NOTE]
>  Web フォームで使用する複合コントロールを作成する場合は、「[Developing Custom ASP.NET Server Controls](../Topic/Developing%20Custom%20ASP.NET%20Server%20Controls.md)」を参照してください。  
>   
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### 複合コントロールを作成するには  
  
1.  `DemoControlHost` という新しい **Windows アプリケーション** プロジェクトを開きます。  
  
2.  **\[プロジェクト\]** メニューの **\[ユーザー コントロールの追加\]** をクリックします。  
  
3.  **\[新しい項目の追加\]** ダイアログ ボックスで、クラス ファイル \(.vb ファイルまたは .cs ファイル\) に複合コントロールの名前を付けます。  
  
4.  **\[追加\]** をクリックして複合コントロールのクラス ファイルを作成します。  
  
5.  コントロールを**ツールボックス**から複合コントロール領域に追加します。  
  
6.  複合コントロールまたはその内在コントロールから発生したイベントを処理するために、イベント プロシージャにコードを記述します。  
  
7.  プロンプトが表示されたら、複合コントロールのデザイナーを閉じ、ファイルを保存します。  
  
8.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
     カスタム コントロールを**ツールボックス**に表示するには、プロジェクトをビルドする必要があります。  
  
9. **ツールボックス**の **\[DemoControlHost\]** タブを使用して、コントロールのインスタンスを `Form1` に追加します。  
  
### コントロール クラス ライブラリを作成するには  
  
1.  新しい **Windows コントロール ライブラリ** プロジェクトを開きます。  
  
     既定では、プロジェクトに複合コントロールが含まれています。  
  
2.  上記の手順に従って、コントロールおよびコードを追加します。  
  
3.  継承したクラスを変更しないコントロールを選択し、このコントロールの **Modifiers** プロパティを **Private** に設定します。  
  
4.  DLL をビルドします。  
  
### コントロール クラス ライブラリの複合コントロールから継承するには  
  
1.  **\[ファイル\]** メニューの **\[追加\]** をポイントし、**\[新しいプロジェクト\]** をクリックして新しい **Windows アプリケーション** プロジェクトをソリューションに追加します。  
  
2.  **ソリューション エクスプローラー**にある新しいプロジェクトの **\[参照設定\]** フォルダーを右クリックし、**\[参照の追加\]** をクリックして **\[参照の追加\]** ダイアログ ボックスを開きます。  
  
3.  **\[プロジェクト\]** タブをクリックし、コントロール ライブラリ プロジェクトをダブルクリックします。  
  
4.  **\[ビルド\]** メニューの **\[ソリューションのビルド\]** をクリックします。  
  
5.  **ソリューション エクスプローラー**でコントロール ライブラリ プロジェクトを右クリックし、ショートカット メニューの **\[新しい項目の追加\]** をクリックします。  
  
6.  **\[新しい項目の追加\]** ダイアログ ボックスの **\[継承されたユーザー コントロール\]** テンプレートをクリックします。  
  
7.  **\[新しい項目の追加\]** ダイアログ ボックスで、継承するコントロールをダブルクリックします。  
  
     新しいコントロールがプロジェクトに追加されます。  
  
8.  新しいコントロールのビジュアル デザイナーを開き、必要な内在コントロールを追加します。  
  
     DLL の複合コントロールから継承された内在コントロールが表示され、**Modifiers** プロパティが **Public** であるコントロールのプロパティを変更できます。  **Modifiers** プロパティが **Private** であるコントロールについては、プロパティを変更できません。  
  
## 参照  
 [チュートリアル : Visual Basic による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)   
 [チュートリアル : Visual C\# による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)   
 [チュートリアル : Visual Basic による Windows フォーム コントロールからの継承](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)   
 [チュートリアル : Visual C\# による Windows フォーム コントロールからの継承](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)   
 [コントロールの種類に関するアドバイス](../../../../docs/framework/winforms/controls/control-type-recommendations.md)   
 [方法 : Windows フォームのコントロールを作成する](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)   
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)