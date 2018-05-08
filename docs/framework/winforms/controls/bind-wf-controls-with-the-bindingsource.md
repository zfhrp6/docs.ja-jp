---
title: '方法 : デザイナーを使用して Windows フォーム コントロールを BindingSource コンポーネントにバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 3acbd17e8e969bb448e6deaf17dec23e44fa3bd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>方法 : デザイナーを使用して Windows フォーム コントロールを BindingSource コンポーネントにバインドする
コントロールがフォームに追加して、アプリケーションのユーザー インターフェイスを決定したら、実行時にユーザーは変更を アプリケーションに関連するデータを保存できるように、データ ソースにコントロールをバインドできます。  
  
 Windows フォーム コントロールまたは一連のコントロールのバインドが最も簡単に使用される、<xref:System.Windows.Forms.BindingSource>コントロールをフォーム上のコントロールとデータ ソース間のブリッジとして。  
  
 フォーム上の 1 つまたは複数のコントロールをデータにバインドできます。次の手順で、<xref:System.Windows.Forms.TextBox>コントロールがデータ ソースにバインドされています。  
  
 手順を実行するには、データベースから派生したデータ ソースにバインドすると見なされます。 その他のデータのストアからデータ ソースを作成する方法の詳細については、次を参照してください。[新しいデータ ソースを追加](/visualstudio/data-tools/add-new-data-sources)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-bind-a-control-at-design-time"></a>デザイン時にコントロールをバインドするには  
  
1.  ドラッグ、<xref:System.Windows.Forms.TextBox>コントロールをフォームにログオンします。  
  
2.  **プロパティ**ウィンドウ。  
  
    1.  展開して、 **(DataBindings)** ノード。  
  
    2.  矢印をクリックして、次に、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティです。  
  
         **データソース**UI 型エディターを開きます。  
  
         プロジェクトまたはフォームのデータ ソースが構成されていた場合は、表示されます。  
  
3.  **[プロジェクト データ ソースの追加]** をクリックしてデータに接続し、データ ソースを作成します。  
  
4.  **データ ソース構成ウィザード**の開始ページで **[次へ]** をクリックします。  
  
5.  **データ ソースの種類を選択して**] ページで、[**データベース**です。  
  
6.  **データ接続の選択** ページで、利用可能な接続の一覧からデータ接続を選択します。 目的のデータ接続が表示されていない場合**新しい接続**新しいデータ接続を作成します。  
  
7.  選択**接続を [はい]、保存**をアプリケーション構成ファイルで、接続文字列を保存します。  
  
8.  アプリケーションで使用するデータベース オブジェクトを選択します。 この場合、希望するテーブルのフィールドを選択、<xref:System.Windows.Forms.TextBox>を表示します。  
  
9. 必要な場合は、既定のデータセット名を変更します。  
  
10. **[完了]** をクリックします。  
  
11. **プロパティ**ウィンドウで、矢印をクリックして、次に、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティをもう一度です。 **データソース**UI 型エディターをバインドするフィールドの名前を選択する、<xref:System.Windows.Forms.TextBox>にします。  
  
     **データソース**UI 型エディターが閉じ、データ セット<xref:System.Windows.Forms.BindingSource>およびテーブル アダプターのデータ接続が、フォームに追加されたことを特定します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [新しいデータ ソースの追加](/visualstudio/data-tools/add-new-data-sources)  
 [データ ソース ウィンドウ](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)
