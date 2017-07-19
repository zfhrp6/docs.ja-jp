---
title: "デザイン時の Windows フォーム コントロールの開発 | Microsoft Docs"
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
  - "Windows フォーム コントロール"
  - "Windows フォーム コントロールを作成します。"
  - "コントロール [Windows フォーム]"
  - "コントロール [Windows フォーム] を作成します。"
  - "ユーザー コントロール [Windows フォーム]"
  - "カスタム コントロール [Windows フォーム]"
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# デザイン時の Windows フォーム コントロールの開発
コントロールの作成者は、.NET Framework は、さまざまなコントロール テクノロジの作成を提供します。 既存のコントロールのコレクションとして機能する複合コントロールのデザインに制限はなくなりました。 継承によって既存の複合コントロールまたは既存の Windows フォーム コントロールから、独自のコントロールを作成できます。 カスタム描画を実装する独自のコントロールを設計することもできます。 これらのオプションには、さまざまなデザインの柔軟性とビジュアル インターフェイスの機能が有効にします。 これらの機能を利用するには、オブジェクト ベースのプログラミング概念について理解ができます。  
  
> [!NOTE]
>  継承、十分に理解する必要はありませんを参照する役に立つ場合があります[NOT IN ビルド: Visual Basic で継承](http://msdn.microsoft.com/ja-jp/e5e6e240-ed31-4657-820c-079b7c79313c)します。  
  
 Web フォームで使用するカスタム コントロールを作成する場合は、[カスタム ASP.NET サーバー コントロールの開発](../Topic/Developing%20Custom%20ASP.NET%20Server%20Controls.md)します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [チュートリアル: Visual Basic による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 Visual Basic で単純な複合コントロールを作成する方法を示します。  
  
 [チュートリアル: Visual c# による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 C# での簡単な複合コントロールを作成する方法を示します。  
  
 [チュートリアル: Visual Basic による Windows フォーム コントロールからの継承](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 Visual Basic で継承を使用して単純な Windows フォーム コントロールを作成する方法を示します。  
  
 [チュートリアル: Visual c# による Windows フォーム コントロールからの継承](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 C# での継承を使用して単純な Windows フォーム コントロールを作成する方法を示します。  
  
 [チュートリアル: Windows 上のスマート タグを使用した一般的なタスクを実行するフォーム コントロール](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 Windows フォーム コントロールのスマート タグの表示機能を使用する方法を示します。  
  
 [チュートリアル: designerserializationvisibilityattribute を標準的な型のコレクションをシリアル化](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 使用する方法を示しています、 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=fullName>属性コレクションをシリアル化します。  
  
 [チュートリアル: カスタム Windows フォーム コントロールのデバッグ デザイン時に](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 Windows フォーム コントロールのデザイン時の動作をデバッグする方法を示します。  
  
 [チュートリアル: Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 複合コントロールをデザイン環境に緊密に統合する方法を示します。  
  
 [方法: Windows フォームのコントロールを作成](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 Windows フォーム コントロールを実装するための考慮事項の概要を示します。  
  
 [方法: 複合コントロールを作成](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 複合コントロールから継承することでコントロールを作成する方法を示します。  
  
 [方法: UserControl クラスを継承](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 複合コントロールを作成する手順の概要を示します。  
  
 [方法: 既存の Windows フォーム コントロールから継承](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 継承して拡張コントロールを作成する方法を示しています、<xref:System.Windows.Forms.Button>クラスを制御します。  
  
 [方法: コントロール クラスから継承](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 拡張コントロールの作成の概要を示します。  
  
 [方法: デザイン時に、コントロールをフォームの端を揃える](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 使用する方法を示しています、<xref:System.Windows.Forms.Control.Dock%2A>プロパティに合わせてそのフォームの端にコントロールを配置します。  
  
 [方法: にコントロールを表示、ツールボックス項目 ダイアログ ボックスの選択](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 表示されるように、コントロールをインストールするための手順を示しています、**ツールボックスのカスタマイズ** ダイアログ ボックス。  
  
 [方法: コントロールにツールボックス ビットマップを指定します。](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 使用する方法を示しています、 <xref:System.Drawing.ToolboxBitmapAttribute>で、カスタム コントロールの横にあるアイコンを表示する、**ツールボックス**します。  
  
 [方法: UserControl の実行時の動作をテストします。](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 使用する方法を示しています、 **UserControl テスト コンテナー**複合コントロールの動作をテストします。  
  
 [Windows フォーム デザイナーでデザイン時エラー](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 意味と、Windows フォーム デザイナーの読み込みに失敗したときに、Microsoft Visual Studio で表示されるデザイン時のエラー リストの使用について説明します。  
  
 [コントロールとコンポーネントの作成のトラブルシューティング](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 診断して、カスタム コンポーネントやコントロールを作成するときに発生する可能性がある一般的な問題を解決する方法を示します。  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Forms.Control?displayProperty=fullName>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=fullName>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
## <a name="related-sections"></a>関連項目  
 [フォーム コントロールの .NET Framework にカスタムの Windows の開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 .NET Framework で独自のカスタム コントロールを作成する方法について説明します。  
  
 [言語非依存および言語非依存コンポーネント](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 作成およびコンポーネントの使用を簡略化するように設計された共通言語ランタイムを紹介します。 この単純さの重要な側面は、さまざまなプログラミング言語で記述されたコンポーネントの間の相互運用性を拡張します。 共通言語仕様 (CLS) では、ツールや複数のプログラミング言語で動作するコンポーネントを作成します。  
  
 [チュートリアル: カスタム コンポーネントを使用して、ツールボックスを自動的に設定します。](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 コンポーネントまたはコントロールに表示されるようにする方法について説明します、**ツールボックスのカスタマイズ** ダイアログ ボックス。