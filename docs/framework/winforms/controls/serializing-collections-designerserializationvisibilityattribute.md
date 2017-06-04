---
title: "チュートリアル : DesignerSerializationVisibilityAttribute を使用した、標準データ型のコレクションのシリアル化 | Microsoft Docs"
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
  - "コレクション, シリアル化"
  - "コレクション, 標準の型"
  - "DesiginerSerializationVisibilityAttribute クラス"
  - "シリアル化, コレクション"
  - "標準の型, コレクション"
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# チュートリアル : DesignerSerializationVisibilityAttribute を使用した、標準データ型のコレクションのシリアル化
カスタム コントロールは、コレクションをプロパティとして公開することがあります。  このチュートリアルでは、<xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> クラスを使用して、デザイン時にコレクションのシリアル化を制御する方法について説明します。  コレクション プロパティに <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> 値を適用すると、プロパティが確実にシリアル化されます。  
  
 このトピックのコードを単一のリストとしてコピーするには、「[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](../Topic/How%20to:%20Serialize%20Collections%20of%20Standard%20Types%20with%20the%20DesignerSerializationVisibilityAttribute.md)」を参照してください。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## 必須コンポーネント  
 このチュートリアルを完了するための要件は次のとおりです。  
  
-   Visual Studio がインストールされているコンピューターで、Windows フォーム アプリケーション プロジェクトを作成および実行するための十分なアクセス許可が付与されていること。  
  
## シリアル化可能なコレクションを持つコントロールの作成  
 最初に、シリアル化可能なコレクションをプロパティとして持つコントロールを作成します。  このコレクションの内容は、**コレクション エディター**を使用して編集できます。コレクション エディターには、**\[プロパティ\]** ウィンドウがからアクセスできます。  
  
#### シリアル化可能なコレクションを持つコントロールを作成するには  
  
1.  `SerializationDemoControlLib` という名前の Windows コントロール ライブラリ プロジェクトを作成します。  詳細については、「[Windows Control Library Template](http://msdn.microsoft.com/ja-jp/722f4e2d-1310-4ed5-8f33-593337ab66b4)」を参照してください。  
  
2.  `UserControl1` の名前を `SerializationDemoControl` に変更します。  詳細については、「[How to: Rename Identifiers](http://msdn.microsoft.com/ja-jp/2430f732-2b70-4516-8cf6-a7bb71cc9724)」を参照してください。  
  
3.  **\[プロパティ\]** ウィンドウで、<xref:System.Windows.Forms.Padding.All%2A?displayProperty=fullName> プロパティの値を `10` に設定します。  
  
4.  <xref:System.Windows.Forms.TextBox> コントロールを `SerializationDemoControl` に配置します。  
  
5.  <xref:System.Windows.Forms.TextBox> コントロールを選択します。  **\[プロパティ\]** ウィンドウで、次のプロパティを設定します。  
  
    |プロパティ|変更後の値|  
    |-----------|-----------|  
    |**Multiline**|`true`|  
    |**Dock**|<xref:System.Windows.Forms.DockStyle>|  
    |**ScrollBars**|<xref:System.Windows.Forms.ScrollBars>|  
    |**ReadOnly**|`true`|  
  
6.  **コード エディター**を使用して、`stringsValue` という名前の文字列配列フィールドを `SerializationDemoControl` で宣言します。  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  `SerializationDemoControl` の `Strings` プロパティを定義します。  
  
> [!NOTE]
>  <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> 値を使用して、コレクションのシリアル化を有効にします。  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  F5 キーを押してプロジェクトをビルドし、**ユーザー コントロール テスト コンテナー**でコントロールを実行します。  
  
2.  **ユーザー コントロール テスト コンテナー**の <xref:System.Windows.Forms.PropertyGrid> で、`Strings` プロパティを探します。  `Strings` プロパティをクリックし、省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックして、**文字列コレクション エディター**を開きます。  
  
3.  **文字列コレクション エディター**にいくつかの文字列を入力します。  各文字列の末尾で Enter キーを押して区切ります。  文字列を入力したら、**\[OK\]** をクリックします。  
  
> [!NOTE]
>  入力した文字列が `SerializationDemoControl` の <xref:System.Windows.Forms.TextBox> に表示されます。  
  
## コレクション プロパティのシリアル化  
 コントロールのシリアル化動作をテストするには、コントロールをフォームに配置し、**コレクション エディター**を使用してコレクションの内容を変更します。  シリアル化されたコレクションの状態は、**Windows フォーム デザイナー**によるコードの出力先となる特別なデザイナー ファイルで確認できます。  
  
#### コレクションをシリアル化するには  
  
1.  Windows アプリケーション プロジェクトをソリューションに追加します。  プロジェクトに `SerializationDemoControlTest` という名前を付けます。  
  
2.  **\[ツールボックス\]** で、**\[SerializationDemoControlLib コンポーネント\]** という名前のタブを見つけます。  このタブで、`SerializationDemoControl` を探します。  詳細については、「[チュートリアル : ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)」を参照してください。  
  
3.  `SerializationDemoControl` をフォームに配置します。  
  
4.  **\[プロパティ\]** ウィンドウで、`Strings` プロパティを見つけます。  `Strings` プロパティをクリックし、省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックして、**文字列コレクション エディター**を開きます。  
  
5.  **文字列コレクション エディター**にいくつかの文字列を入力します。  各文字列の末尾で Enter キーを押して区切ります。  文字列を入力したら、**\[OK\]** をクリックします。  
  
> [!NOTE]
>  入力した文字列が `SerializationDemoControl` の <xref:System.Windows.Forms.TextBox> に表示されます。  
  
1.  **ソリューション エクスプローラー**の **\[すべてのファイルを表示\]** をクリックします。  
  
2.  **\[Form1\]** ノードを開きます。  このノードの下に、**Form1.Designer.cs** または **Form1.Designer.vb** というファイルが表示されます。  **Windows フォーム デザイナー**は、このファイルにフォームと子コントロールのデザイン時の状態を表すコードを出力します。  **コード エディター**でこのファイルを開きます。  
  
3.  **Windows Form Designer generated code** という領域を開き、**serializationDemoControl1** というラベルが付けられたセクションを見つけます。  このラベルの下が、コントロールのシリアル化状態を表すコードです。  手順 5. で入力した文字列が、`Strings` プロパティへの代入として表示されます。  たとえば、文字列として "red"、"orange"、および "yellow" を入力した場合には、次のようなコードが表示されます。  
  
4.  \[Visual Basic\]  
  
    ```  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```  
  
5.  \[C\#\]  
  
    ```  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
  
6.  **コード エディター**で、`Strings` プロパティの <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> の値を <xref:System.ComponentModel.DesignerSerializationVisibility> に変更します。  
  
7.  \[Visual Basic\]  
  
    ```  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
8.  \[C\#\]  
  
    ```  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
  
9. ソリューションを再度ビルドし、手順 4. から 8. を繰り返します。  
  
> [!NOTE]
>  この場合、**Windows フォーム デザイナー**は、`Strings` プロパティへの代入を出力しません。  
  
## 次の手順  
 標準データ型のコレクションをシリアル化する方法がわかったら、カスタム コントロールをデザイン時環境により深く統合することを検討してください。  以下のトピックでは、カスタム コントロールのデザイン時の統合を強化する方法について説明しています。  
  
-   [Design\-Time Architecture](../Topic/Design-Time%20Architecture.md)  
  
-   [Windows フォーム コントロールの属性](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [Designer Serialization Overview](../Topic/Designer%20Serialization%20Overview.md)  
  
-   [チュートリアル : Visual Studio のデザイン時機能を活用した Windows フォーム コントロールの作成](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## 参照  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>   
 [Designer Serialization Overview](../Topic/Designer%20Serialization%20Overview.md)   
 [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](../Topic/How%20to:%20Serialize%20Collections%20of%20Standard%20Types%20with%20the%20DesignerSerializationVisibilityAttribute.md)   
 [チュートリアル : ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)