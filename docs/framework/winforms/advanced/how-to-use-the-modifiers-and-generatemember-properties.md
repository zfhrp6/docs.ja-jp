---
title: "方法 : Modifiers プロパティおよび GenerateMember プロパティを使用する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_GenerateMember"
  - "Designer_Modifiers"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "基本フォーム"
  - "フォームの継承"
  - "GenerateMember プロパティ"
  - "継承, フォーム"
  - "継承フォーム"
  - "継承フォーム, Windows フォーム"
  - "Modifiers プロパティ"
  - "Windows フォーム, 継承"
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : Modifiers プロパティおよび GenerateMember プロパティを使用する
Windows フォームにコンポーネントを配置するときに、デザイン環境では `GenerateMember` プロパティと `Modifiers` プロパティを使用できます。  `GenerateMember` プロパティは、Windows フォーム デザイナーでコンポーネントにメンバー変数を生成するときに指定します。  `Modifiers` プロパティは、そのメンバー変数に割り当てるアクセス修飾子です。  `GenerateMember` プロパティの値が `false` の場合、`Modifiers` プロパティの値は無効です。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### コンポーネントがフォームのメンバーかどうかを指定するには  
  
1.  Windows フォーム デザイナーで、フォームを開きます。  
  
2.  **ツールボックス**を開き、3 つの <xref:System.Windows.Forms.Button> コントロールをフォームに配置します。  
  
3.  <xref:System.Windows.Forms.Button> コントロールの `GenerateMember` プロパティと `Modifiers` プロパティを、次の表に示した値に設定します。  
  
    |ボタン名|GenerateMember 値|Modifiers 値|  
    |----------|----------------------|-----------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|変更なし|  
  
4.  ソリューションをビルドします。  
  
5.  **ソリューション エクスプローラー**の **\[すべてのファイルを表示\]** をクリックします。  
  
6.  **\[Form1\]** ノードを開き、**コード エディター**で、**Form1.Designer.vb** ファイルまたは **Form1.Designer.cs** ファイルを開きます。  このファイルには、Windows フォーム デザイナーからコードが出力されます。  
  
7.  3 つのボタンの宣言を探します。  `GenerateMember` プロパティと `Modifiers` プロパティの指定による違いを以下のコード例に示します。  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  Windows フォーム デザイナーは、<xref:System.Windows.Forms.Panel> などのコンテナー コントロールに既定で `private` \(Visual Basic では `Friend`\) 修飾子を割り当てます。  ベースの <xref:System.Windows.Forms.UserControl> または <xref:System.Windows.Forms.Form> にコンテナー コントロールが含まれていても、継承されたコントロールやフォームで新しい子を追加することはできません。  これを解決するには、ベースのコンテナー コントロールの修飾子を `protected` または `public` に変更します。  
  
## 参照  
 <xref:System.Windows.Forms.Button>   
 [Windows フォームのビジュアルの継承](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)   
 [チュートリアル : ビジュアル継承のデモンストレーション](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)   
 [方法 : Windows フォームを継承する](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)