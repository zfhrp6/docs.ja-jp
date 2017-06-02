---
title: "方法 : Windows フォームに単純バインド コントロールを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "データ バインド, 単純データ バインディング"
  - "Windows フォーム コントロール, データ バインド"
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : Windows フォームに単純バインド コントロールを作成する
*単純バインディング*を使用すると、データセット テーブルの列の値など、1 つのデータ要素をコントロールで表示できます。  コントロールの任意のプロパティをデータ値に単純連結できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### コントロールを単純連結するには  
  
1.  データ ソースに接続する。  詳細については、「[データ ソースへの接続](../../../docs/framework/data/adonet/connecting-to-a-data-source.md)」を参照してください。  
  
2.  フォームでコントロールを選択し、**\[プロパティ\]** ウィンドウを表示します。  
  
3.  **\(DataBindings\)** プロパティを展開します。  
  
     頻繁に連結されるプロパティが **\(DataBindings\)** プロパティの下に表示されます。  たとえば、ほとんどのコントロールでは、**Text** プロパティが最も頻繁に連結されます。  
  
4.  連結しようとしているプロパティが一般によく連結されるプロパティでない場合は、**\[詳細\]** ボックスの**省略記号ボタン** \(![VisualStudioEllipsesButton スクリーンショット](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックして、**\[フォーマットと詳細バインド\]** ダイアログ ボックスを表示します。このダイアログ ボックスには、選択したコントロールのプロパティの完全な一覧が表示されます。  
  
5.  連結するプロパティを選択し、**\[バインド\]** の下にあるドロップダウン矢印をクリックします。  
  
     使用できるデータ ソースの一覧が表示されます。  
  
6.  目的の 1 つのデータ要素が見つかるまで、連結先のデータ ソースを展開します。  たとえば、データセットのテーブル内の列の値に連結する場合は、データセットの名前を展開し、次にテーブル名を展開して、列名を表示します。  
  
7.  連結先の要素の名前をクリックします。  
  
8.  **\[フォーマットと詳細バインド\]** ダイアログ ボックスで作業している場合は、**\[OK\]** をクリックして **\[プロパティ\]** ウィンドウに戻ります。  
  
9. コントロールのほかのプロパティも連結する場合は、手順 3 ～ 7 を繰り返します。  
  
    > [!NOTE]
    >  単純連結コントロールは 1 つのデータ要素だけを表示するため、単純連結コントロールを含む Windows フォームにはデータ間で移動するためのロジックを含めるのが一般的です。  
  
## 参照  
 <xref:System.Windows.Forms.Binding>   
 [Windows フォームでのデータ バインド](../../../docs/framework/winforms/windows-forms-data-binding.md)   
 [データ連結と Windows フォーム](../../../docs/framework/winforms/data-binding-and-windows-forms.md)