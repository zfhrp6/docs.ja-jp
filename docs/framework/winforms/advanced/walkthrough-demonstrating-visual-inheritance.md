---
title: 'チュートリアル : ビジュアル継承のデモンストレーション'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: 61239d9b547be73a14618d41feeb9aeea9f8ded6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529702"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>チュートリアル : ビジュアル継承のデモンストレーション
ビジュアル継承により、基本フォームのコントロールを表示して、新しいコントロールを追加できます。 このチュートリアルでは、基本フォームを作成してクラス ライブラリにコンパイルします。 このクラス ライブラリを別のプロジェクトにインポートして、基本フォームから継承する新しいフォームを作成します。 このチュートリアルでは、次の作業を行う方法について説明します。  
  
-   基本フォームを含むクラス ライブラリ プロジェクトを作成します。  
  
-   基本フォームの派生クラスが変更できるプロパティを持つボタンを追加します。  
  
-   基本フォームの継承元により変更できないボタンを追加します。  
  
-   `BaseForm` から継承したフォームを含むプロジェクトを作成します。  
  
 最終的には、このチュートリアルでは、継承されたフォーム上のプライベート コントロールとプロテクト コントロールの違いを示します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
> [!CAUTION]
>  すべてのコントロールが基本フォームのビジュアル継承をサポートするわけではありません。 次のコントロールでは、このチュートリアルで説明するシナリオはサポートされません。  
>   
>  <xref:System.Windows.Forms.WebBrowser>  
>   
>  <xref:System.Windows.Forms.ToolStrip>  
>   
>  <xref:System.Windows.Forms.ToolStripPanel>  
>   
>  <xref:System.Windows.Forms.TableLayoutPanel>  
>   
>  <xref:System.Windows.Forms.FlowLayoutPanel>  
>   
>  <xref:System.Windows.Forms.DataGridView>  
>   
>  継承されたフォームのこれらのコントロールは、使用する修飾子 (`private`、`protected`、または `public`) に関係なく、常に読み取り専用です。  
  
## <a name="scenario-steps"></a>シナリオの手順  
 最初の手順では、基本フォームを作成します。  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a>基本フォームを含むクラス ライブラリ プロジェクトを作成するには  
  
1.  **ファイル** メニューの 選択**新規**、し**プロジェクト**を開くには、**新しいプロジェクト** ダイアログ ボックス。  
  
2.  という名前の Windows フォーム アプリケーションを作成する`BaseFormLibrary`です。  
  
3.  標準の Windows フォーム アプリケーションではなく、クラス ライブラリを作成する**ソリューション エクスプ ローラー**を右クリックし、 **BaseFormLibrary**プロジェクト ノードを選択し、 **のプロパティ**.  
  
4.  プロジェクトのプロパティで、変更、**出力の種類**から**Windows アプリケーション**に**クラス ライブラリ**です。  
  
5.  **ファイル**] メニューの [選択**すべて保存**を既定の場所に、プロジェクト ファイルとファイルを保存します。  
  
 次の 2 つの手順では、基本フォームにボタンを追加します。 ビジュアル継承を示すには、`Modifiers` プロパティを設定して、ボタンに異なるアクセス レベルを付与します。  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a>基本フォームの継承クラスから変更が可能なボタンを追加するには  
  
1.  開いている**Form1**デザイナーでします。  
  
2.  **すべての Windows フォーム**のタブ、**ツールボックス**をダブルクリックして**ボタン**をフォームにボタンを追加します。 マウスを使用し、ボタンを配置してサイズを変更します。  
  
3.  [プロパティ] ウィンドウで、ボタンの次のプロパティを設定します。  
  
    -   設定、**テキスト**プロパティを**Say こんにちは**です。  
  
    -   設定、 **(名)** プロパティを**btnProtected**です。  
  
    -   設定、**修飾子**プロパティを**Protected**です。 継承するフォームができるようになります**Form1**のプロパティを変更する**btnProtected**です。  
  
4.  ダブルクリックして、 **Say こんにちは**のイベント ハンドラーを追加するボタン、 **をクリックして**イベント。  
  
5.  イベント ハンドラーに次のコードを追加します。  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>基本フォームの継承元により変更できないボタンを追加するには  
  
1.  クリックしてデザイン ビューに切り替え、 **Form1.vb [デザイン]、Form1.cs [デザイン]、または Form1.jsl の [デザイン]** コード エディターの上または F7 キーを押してタブです。  
  
2.  2 番目のボタンを追加し、そのプロパティを次のように設定します。  
  
    -   設定、**テキスト**プロパティを**Say Goodbye**です。  
  
    -   設定、 **(名)** プロパティを**btnPrivate**です。  
  
    -   設定、**修飾子**プロパティを**プライベート**です。 継承するフォームが不可能になります。 **Form1**のプロパティを変更する**btnPrivate**です。  
  
3.  ダブルクリックして、 **Say Goodbye**のイベント ハンドラーを追加するボタン、 **をクリックして**イベント。 イベントの手順で、次のコード行を配置します。  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  **ビルド**] メニューの [選択**BaseForm ライブラリのビルド**クラス ライブラリをビルドします。  
  
     ライブラリがビルドされたら、作成したフォームから継承する新しいプロジェクトを作成できます。  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>基本フォームから継承したフォームを含むプロジェクトを作成するには  
  
1.  **ファイル** メニューの 選択**追加**し**新しいプロジェクト**を開くには、**新しいプロジェクトの追加** ダイアログ ボックス。  
  
2.  という名前の Windows フォーム アプリケーションを作成する`InheritanceTest`です。  
  
#### <a name="to-add-an-inherited-form"></a>継承されたフォームを追加するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **InheritanceTest**プロジェクトで、**追加**、し、**新しい項目の**します。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、 **Windows フォーム**カテゴリ (カテゴリの一覧の場合) クリックし、**継承されたフォーム**テンプレート。  
  
3.  既定の名前のままにして`Form2` をクリックし、**追加**です。  
  
4.  **継承ピッカー**ダイアログ ボックスで、 **Form1**から、 **BaseFormLibrary**フォームから継承し、をクリックするとプロジェクト**OK**.  
  
     これでフォームを作成、 **InheritanceTest**プロジェクトのフォームから派生した**BaseFormLibrary**です。  
  
5.  継承されたフォームを開きます (**Form2**) がまだ開いていない場合をダブルクリックしてデザイナーでします。  
  
     デザイナーで、継承されたボタンにシンボルがある (![VisualBasicInheritanceSymbol スクリーン ショット](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) を示す継承され、上の隅にします。  
  
6.  選択、 **Say こんにちは**ボタンをクリックし、サイズ変更ハンドルを観察します。 このボタンは保護されているため、継承元が、移動、サイズ変更、キャプションの変更、およびその他の変更を実行できます。  
  
7.  プライベート**Say Goodbye**  ボタン、およびサイズ変更ハンドルがないことに注意してください。 また、、**プロパティ**ウィンドウで、このボタンのプロパティは変更できないことを示すためにグレー表示にします。  
  
8.  Visual C# の場合: 使用している場合  
  
    1.  **ソリューション エクスプ ローラー**を右クリックして**Form1**で、 **InheritanceTest**プロジェクトし、**削除**です。 表示されるメッセージ ボックスで、をクリックして**OK**削除を確認します。  
  
    2.  Program.cs ファイルを開き、行 `Application.Run(new Form1());` を `Application.Run(new Form2());` に変更します。  
  
9. **ソリューション エクスプ ローラー**を右クリックし、 **InheritanceTest**プロジェクトし、選択**スタートアップ プロジェクトとして設定**です。  
  
10. **ソリューション エクスプ ローラー**を右クリックし、 **InheritanceTest**プロジェクトし、選択**プロパティ**です。  
  
11. **InheritanceTest**プロパティ ページ、設定、**スタートアップ オブジェクト**継承されたフォーム (**Form2**)。  
  
12. F5 を押してアプリケーションを実行し、継承されたフォームの動作を確認します。  
  
## <a name="next-steps"></a>次の手順  
 ユーザー コントロールの継承はほぼ同じ方法で機能します。 新しいクラス ライブラリ プロジェクトを開き、ユーザー コントロールを追加します。 内在コントロールを配置し、プロジェクトをコンパイルします。 別の新しいクラス ライブラリ プロジェクトを開き、コンパイル済みのクラス ライブラリへの参照を追加します。 また、[継承されたコントロールを追加してみてください (を通じて、**新しい項目の追加**] ダイアログ ボックス) をプロジェクトを使用して、**継承ピッカー**です。 ユーザー コントロールを追加し、変更、 `Inherits` (`:` Visual c#) ステートメントです。 詳細については、次を参照してください。[する方法: Windows フォームの継承](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: Windows フォームを継承する](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [Windows フォームのビジュアルの継承](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [Windows フォーム](../../../../docs/framework/winforms/index.md)
