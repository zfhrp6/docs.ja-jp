---
title: "チュートリアル: DesignerSerializationVisibilityAttribute を使用した、標準データ型のコレクションのシリアル化"
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
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9efad2da27f4003632b643b9f5f0602be0d55480
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a>チュートリアル: DesignerSerializationVisibilityAttribute を使用した、標準データ型のコレクションのシリアル化
カスタム コントロールは、プロパティとして、コレクションを公開して場合があります。 このチュートリアルを使用する方法を示します、<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>クラスをデザイン時にコレクションをシリアル化する方法を制御します。 適用する、<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content>値をコレクション プロパティにより、プロパティをシリアル化することです。  
  
 このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: シリアル化するコレクションの標準の型、designerserializationvisibilityattribute を](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## <a name="prerequisites"></a>必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   作成し、Visual Studio がインストールされているコンピューターで Windows フォーム アプリケーション プロジェクトを実行できる十分なアクセスを許可します。  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a>シリアル化可能なコレクションを含むコントロールを作成します。  
 最初の手順では、コントロールのプロパティとしてシリアル化可能なコレクションを作成します。 使用してこのコレクションの内容を編集することができます、**コレクション エディター**からにアクセスできる、**プロパティ**ウィンドウです。  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a>シリアル化可能なコレクションを使用してコントロールを作成するには  
  
1.  いう Windows コントロール ライブラリ プロジェクトを作成する`SerializationDemoControlLib`です。 詳細については、次を参照してください。 [Windows コントロール ライブラリ テンプレート](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4)です。  
  
2.  名前を変更`UserControl1`に`SerializationDemoControl`です。 詳細については、次を参照してください。[する方法: 識別子の名前を変更](http://msdn.microsoft.com/en-us/2430f732-2b70-4516-8cf6-a7bb71cc9724)です。  
  
3.  **プロパティ**ウィンドウで、設定の値、<xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType>プロパティを`10`です。  
  
4.  場所、<xref:System.Windows.Forms.TextBox>内の制御、`SerializationDemoControl`です。  
  
5.  <xref:System.Windows.Forms.TextBox> コントロールを選択します。 **プロパティ**ウィンドウで、次のプロパティを設定します。  
  
    |プロパティ|変更後の値|  
    |--------------|---------------|  
    |**Multiline**|`true`|  
    |**ドッキング ステーション**|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |**スクロール バー**|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |**ReadOnly**|`true`|  
  
6.  **コード エディター**、という名前の文字列配列フィールドは宣言`stringsValue`で`SerializationDemoControl`です。  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  定義、`Strings`プロパティを`SerializationDemoControl`です。  
  
> [!NOTE]
>  <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content>値を使用して、コレクションのシリアル化を有効にします。  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  F5 キーを押してプロジェクトをビルドし、**UserControl Test Container** でコントロールを実行します。  
  
2.  検索、`Strings`プロパティに、<xref:System.Windows.Forms.PropertyGrid>の**UserControl テスト コンテナー**です。 をクリックして、`Strings`プロパティ、省略記号ボタンをクリックして (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) を開く ボタン、 **文字列コレクションエディター**.  
  
3.  いくつかの文字列を入力、**文字列コレクション エディター**です。 各文字列の最後に ENTER キーを押すと、それらを区切ります。 をクリックして**OK**文字列の入力が完了したらです。  
  
> [!NOTE]
>  入力した文字列に表示されます、<xref:System.Windows.Forms.TextBox>の`SerializationDemoControl`です。  
  
## <a name="serializing-a-collection-property"></a>コレクション プロパティをシリアル化します。  
 コントロールのシリアル化の動作をテストするには、フォームに配置し、使用して、コレクションの内容を変更、**コレクション エディター**です。 先に特別なデザイナー ファイルを調べることで、シリアル化されたコレクションの状態を確認できます、 **Windows フォーム デザイナー**はコードを出力します。  
  
#### <a name="to-serialize-a-collection"></a>コレクションをシリアル化するには  
  
1.  Windows アプリケーション プロジェクトをソリューションに追加します。 プロジェクトに `SerializationDemoControlTest` という名前を付けます。  
  
2.  **ツールボックス**、という名前のタブを見つける**SerializationDemoControlLib コンポーネント**です。 このタブに表示されます、`SerializationDemoControl`です。 詳細については、「[チュートリアル: ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)」を参照してください。  
  
3.  場所、`SerializationDemoControl`フォーム上でします。  
  
4.  検索、`Strings`プロパティに、**プロパティ**ウィンドウです。 をクリックして、`Strings`プロパティ、省略記号ボタンをクリックして (![VisualStudioEllipsesButton スクリーン ショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) を開く ボタン、 **文字列コレクションエディター**.  
  
5.  内のいくつかの文字列を入力、**文字列コレクション エディター**です。 各文字列の最後に ENTER キーを押すと、それらを区切ります。 をクリックして**OK**文字列の入力が完了したらです。  
  
> [!NOTE]
>  入力した文字列に表示されます、<xref:System.Windows.Forms.TextBox>の`SerializationDemoControl`です。  
  
1.  **ソリューション エクスプローラー**で、**[すべてのファイルを表示]** ボタンをクリックします。  
  
2.  開く、 **Form1**ノード。 という名前のファイルは、その下に**Form1.Designer.cs**または**Form1.Designer.vb**です。 これは、ファイルに、 **Windows フォーム デザイナー**フォームとその子コントロールのデザイン時の状態を表すコードを出力します。 このファイルを**コード エディター**で開きます。  
  
3.  呼ばれる領域を開く**Windows フォーム デザイナーで生成されたコード**というラベルの付いたセクションを見つけて**serializationDemoControl1**です。 このラベルの下には、コントロールのシリアル化された状態を表すコードです。 代入に表示される手順 5. で入力した文字列、`Strings`プロパティです。 C# および Visual Basic では、次のコード例は、表示される内容、文字列"red"、「オレンジ」、および「黄」を入力した場合のようなコードを表示します。  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  **コード エディター**の値を変更、<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>上、`Strings`プロパティを<xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>です。  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. ソリューションと手順 3. および 4. を再構築します。  
  
> [!NOTE]
>  ここで、 **Windows フォーム デザイナー**への割り当ては出力されません、`Strings`プロパティです。  
  
## <a name="next-steps"></a>次の手順  
 標準の型のコレクションをシリアル化する方法がわかればは、カスタム コントロールをデザイン時環境により密接に統合することを検討します。 次のトピックでは、カスタム コントロールのデザイン時の統合を強化する方法について説明します。  
  
-   [デザイン時アーキテクチャ](http://msdn.microsoft.com/library/4881917b-628f-4689-b872-472e4f8a4e3a)  
  
-   [Windows フォーム コントロールの属性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [デザイナーのシリアル化の概要](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
  
-   [チュートリアル: Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>  
 [デザイナーのシリアル化の概要](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
 [方法: designerserializationvisibilityattribute を使用、標準的なデータ型のコレクションをシリアル化](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)  
 [チュートリアル: ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
