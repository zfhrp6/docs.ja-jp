---
title: "コントロールとコンポーネントの作成時のトラブルシューティング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- troubleshooting components
- troubleshooting controls [Windows Forms]
- controls [Windows Forms], troubleshooting
- components [Windows Forms], troubleshooting
- Windows Forms controls, debugging
ms.assetid: e9c8c099-2271-4737-882f-50f336c7a55e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e027a5b60e066a8d38db530c37a394227f2e892
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-control-and-component-authoring"></a>コントロールとコンポーネントの作成時のトラブルシューティング
このトピックでは、コンポーネントとコントロールの開発時に発生する次の一般的な問題について説明します。 詳細については、「[コンポーネントによるプログラミング](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)」を参照してください。  
  
-   ツールボックスにコントロールを追加できない  
  
-   Windows フォームのユーザー コントロールまたはコンポーネントをデバッグできない  
  
-   継承されたコントロールまたはコンポーネントでイベントが 2 回発生する  
  
-   デザイン時エラー: "コンポーネント '*コンポーネント名*' を生成できませんでした"  
  
-   STAThreadAttribute  
  
-   ツールボックスにコンポーネント アイコンが表示されない  
  
## <a name="cannot-add-control-to-toolbox"></a>ツールボックスにコントロールを追加できない  
 別のプロジェクトで作成したカスタム コントロールまたはサード パーティ製コントロールを**ツールボックス**に追加する場合は、手動で追加する必要があります。 現在のプロジェクトにコントロールまたはコンポーネントが含まれている場合は、**ツールボックス**に自動的に表示されます。 詳細については、「[チュートリアル : ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)」を参照してください。  
  
#### <a name="to-add-a-control-to-the-toolbox"></a>ツールボックスにコントロールを追加するには  
  
1.  **[ツールボックス]** を右クリックし、ショートカット メニューの **[アイテムの選択]** をクリックします。  
  
2.  **[ツールボックス アイテムの選択]** ダイアログ ボックスで、コンポーネントを追加します。  
  
    -   .NET Framework コンポーネントまたはコントロールを追加する場合は、**[.NET Framework コンポーネント]** タブをクリックします。  
  
         または  
  
    -   COM コンポーネントまたは ActiveX コントロールを追加する場合は、**[COM コンポーネント]** タブをクリックします。  
  
3.  ダイアログ ボックスにコントロールが表示されている場合は、コントロールが選択されていることを確認し、**[OK]** をクリックします。  
  
     コントロールが**ツールボックス**に追加されます。  
  
4.  ダイアログ ボックスにコントロールが表示されていない場合は、次の手順を実行します。  
  
    1.  **[参照]** ボタンをクリックします。  
  
    2.  コントロールが含まれた .dll ファイルがあるフォルダーを参照します。  
  
    3.  .dll ファイルを選択し、**[開く]** をクリックします。  
  
         ダイアログ ボックスにコントロールが表示されます。  
  
    4.  コントロールが選択されていることを確認し、**[OK]** をクリックします。  
  
         コントロールが**ツールボックス**に追加されます。  
  
## <a name="cannot-debug-the-windows-forms-user-control-or-component"></a>Windows フォームのユーザー コントロールまたはコンポーネントをデバッグできない  
 コントロールがから派生している場合、<xref:System.Windows.Forms.UserControl>クラス、テスト コンテナーで実行時の動作をデバッグすることができます。 詳細については、「[方法: UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。  
  
 他のカスタム コントロールやカスタム コンポーネントはスタンドアロン プロジェクトではありません。 そのため、Windows フォーム プロジェクトなどのアプリケーションでホストする必要があります。 コントロールまたはコンポーネントをデバッグするには、Windows フォーム プロジェクトに追加する必要があります。  
  
#### <a name="to-debug-a-control-or-component"></a>コントロールまたはコンポーネントをデバッグするには  
  
1.  **[ビルド]** メニューの **[ソリューションのビルド]** をクリックして、ソリューションをビルドします。  
  
2.  **[ファイル]** メニューの **[追加]** をクリックし、**[新しいプロジェクト]** をクリックして、アプリケーションにテスト プロジェクトを追加します。  
  
3.  **[新しいプロジェクトの追加]** ダイアログ ボックスで、プロジェクトの種類として **[Windows アプリケーション]** を選択します。  
  
4.  **ソリューション エクスプローラー**で、新しいプロジェクトの **[参照設定]** ノードを右クリックします。 ショートカット メニューの **[参照の追加]** をクリックして、コントロールまたはコンポーネントを含むプロジェクトへの参照を追加します。  
  
5.  テスト プロジェクトにコントロールまたはコンポーネントのインスタンスを作成します。 コンポーネントが**ツールボックス**に表示されている場合は、デザイナー画面にドラッグできます。または、次のコード例に示すように、インスタンスをプログラムで作成できます。  
  
    ```vb  
    Dim Component1 As New MyNeatComponent()  
    ```  
  
    ```csharp  
    MyNeatComponent Component1 = new MyNeatComponent();  
    ```  
  
     これで、コントロールまたはコンポーネントを通常どおりデバッグできるようになります。  
  
 デバッグの詳細については、「[Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio)」および「[チュートリアル : カスタム Windows フォーム コントロールのデザイン時のデバッグ](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)」を参照してください。  
  
## <a name="event-is-raised-twice-in-inherited-control-or-component"></a>継承されたコントロールまたはコンポーネントでイベントが 2 回発生する  
 `Handles` 句が重複していることが原因と考えられます。 詳細については、「[Visual Basic での継承されたイベント ハンドラーのトラブルシューティング](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)」を参照してください。  
  
## <a name="design-time-error-failed-to-create-component-component-name"></a>デザイン時エラー: "コンポーネント 'コンポーネント名' を生成できませんでした"  
 コンポーネントまたはコントロールは、パラメーターなしで既定のコンストラクターを提供する必要があります。 デザイン環境では、コンポーネントまたはコントロールのインスタンスを作成するときに、パラメーターを受け取るコンストラクター オーバーロードにパラメーターを提供しません。  
  
## <a name="stathreadattribute"></a>STAThreadAttribute  
 <xref:System.STAThreadAttribute> Windows フォームがシングル スレッド アパートメント モデルを使用する共通言語ランタイム (CLR) に通知します。 この属性を Windows フォーム アプリケーションの `Main` メソッドに適用していない場合、意図しない動作が発生することがあります。 たとえば、背景画像されない可能性がありますなどのコントロールに対して<xref:System.Windows.Forms.ListView>です。 また、一部のコントロールでは、オートコンプリートやドラッグ アンド ドロップの動作を正常に行うためにこの属性が必要になる場合もあります。  
  
## <a name="component-icon-does-not-appear-in-toolbox"></a>ツールボックスにコンポーネント アイコンが表示されない  
 使用すると<xref:System.Drawing.ToolboxBitmapAttribute>にカスタム コンポーネントにアイコンを関連付けるには、ビットマップは自動生成されたコンポーネントをツールボックスに表示されません。 ビットマップを表示するには、**[ツールボックス アイテムの選択]** ダイアログ ボックスを使用してコントロールを再読み込みします。 詳細については、「[方法 : コントロールにツールボックス ビットマップを指定する](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [デザイン時の Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [チュートリアル: ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 [方法: UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 [チュートリアル: カスタム Windows フォーム コントロールのデザイン時のデバッグ](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 [コンポーネントの作成](http://msdn.microsoft.com/library/4a5a5e49-0378-4a31-83bc-24da0f1a727d)  
 [デザイン時の開発のトラブルシューティング](http://msdn.microsoft.com/library/e048d08e-fa7c-4be8-b238-4abaa199a0a6)  
 [コンポーネントによるプログラミング](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)
