---
title: デザイン時の Windows フォーム コントロールの開発
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
ms.openlocfilehash: 267a56cbfd9025e2e20f1468535e5544146535a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="developing-windows-forms-controls-at-design-time"></a>デザイン時の Windows フォーム コントロールの開発
コントロールの作成者は、.NET Framework のさまざまなコントロール作成テクノロジを利用できます。 既存のコントロールを組み合わせた複合コントロールしかデザインできないといった制約はなくなりました。 継承により、既存の複合コントロールや既存の Windows フォーム コントロールから、独自のコントロールを作成できます。 カスタム描画を実装する独自のコントロールを設計することもできます。 これらのオプションを使うと、非常に柔軟にビジュアル インターフェイスのデザインと機能を決めることができます。 これらの機能を利用するには、オブジェクト ベースのプログラミング概念について理解しておく必要があります。  
  
> [!NOTE]
>  継承、十分に理解する必要はありませんを参照する役に立つ場合があります[継承の基礎 (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)です。  
  
 Web フォームで使うカスタム コントロールを作る場合は、「[カスタム ASP.NET サーバー コントロールの開発](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef)」をご覧ください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [チュートリアル: Visual Basic による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 Visual Basic で簡単な複合コントロールを作る方法を示します。  
  
 [チュートリアル: Visual C# による複合コントロールの作成](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 C# で簡単な複合コントロールを作る方法を示します。  
  
 [チュートリアル: Visual Basic による Windows フォーム コントロールからの継承](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 Visual Basic で継承を使って簡単な Windows フォーム コントロールを作る方法を示します。  
  
 [チュートリアル: Visual C# による Windows フォーム コントロールからの継承](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 C# で継承を使って簡単な Windows フォーム コントロールを作る方法を示します。  
  
 [チュートリアル: Windows フォーム コントロールのスマート タグを使用した共通タスクの実行](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 Windows フォーム コントロールでスマート タグ機能を使う方法を示します。  
  
 [チュートリアル: DesignerSerializationVisibilityAttribute を使用した、標準データ型のコレクションのシリアル化](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 使用する方法を示します、<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType>属性、コレクションにシリアル化します。  
  
 [チュートリアル: カスタム Windows フォーム コントロールのデザイン時のデバッグ](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 Windows フォーム コントロールのデザイン時動作をデバッグする方法を示します。  
  
 [チュートリアル: Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 デザイン環境に複合コントロールを緊密に統合する方法を示します。  
  
 [方法: Windows フォームのコントロールを作成する](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 Windows フォーム コントロールの実装に関する考慮事項の概要を説明します。  
  
 [方法: 複合コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 複合コントロールから継承することでコントロールを作る方法を示します。  
  
 [方法: UserControl クラスを継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 複合コントロール作成手順の概要を説明します。  
  
 [方法: 既存の Windows フォーム コントロールから継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 継承することによって拡張コントロールを作成する方法を示しています、<xref:System.Windows.Forms.Button>クラスを制御します。  
  
 [方法: コントロール クラスを継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 拡張コントロールの作成の概要を説明します。  
  
 [方法: デザイン時にフォームの端に合わせてコントロールを配置する](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 使用する方法を示します、<xref:System.Windows.Forms.Control.Dock%2A>プロパティを合わせて、コントロールが占有するフォームの端を配置します。  
  
 [方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 **ツールボックスのカスタマイズ** ダイアログ ボックスに表示されるようにコントロールをインストールする手順を示します。  
  
 [方法: コントロールにツールボックス ビットマップを指定する](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 使用する方法を示します、<xref:System.Drawing.ToolboxBitmapAttribute>で、カスタム コントロールの横にあるアイコンを表示する、**ツールボックス**です。  
  
 [方法: UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 **UserControl テスト コンテナー**を使って複合コントロールの動作をテストする方法を示します。  
  
 [Windows フォーム デザイナーでのデザイン時エラー](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 Windows フォーム デザイナーで読み込みに失敗したときに Microsoft Visual Studio に表示されるデザイン時エラー リストの意味と使用法について説明します。  
  
 [コントロールとコンポーネントの作成時のトラブルシューティング](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 カスタム コンポーネントやコントロールを作るときに発生する可能性がある一般的な問題を診断して解決する方法を示します。  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
## <a name="related-sections"></a>関連項目  
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 .NET Framework で独自のカスタム コントロールを作る方法について説明します。  
  
 [言語への非依存性、および言語非依存コンポーネント](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 コンポーネントの作成と使用を簡略化するように設計されている共通言語ランタイムの概要について説明します。 この簡略化の重要な側面は、さまざまなプログラミング言語で記述されたコンポーネント間の相互運用性の拡張です。 共通言語仕様 (CLS) を使うと、複数のプログラミング言語で動作するツールやコンポーネントを作ることができます。  
  
 [チュートリアル: ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 コンポーネントやコントロールを**ツールボックスのカスタマイズ** ダイアログ ボックスに表示できるようにする方法を説明します。
