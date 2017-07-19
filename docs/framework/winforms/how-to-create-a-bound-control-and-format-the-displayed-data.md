---
title: "方法 : バインド コントロールを作成して表示データの書式を設定する | Microsoft Docs"
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
  - "バインド コントロール [Windows フォーム], 作成"
  - "バインド コントロール [Windows フォーム], 書式設定 (データを)"
  - "データ [Windows フォーム], 書式指定"
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : バインド コントロールを作成して表示データの書式を設定する
Windows フォームのデータ バインディングでは、\[**フォーマットと詳細バインド**\] ダイアログ ボックスを使用してデータ バインド コントロールに表示されるデータの書式を設定できます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### コントロールをバインドして表示データの書式を設定するには  
  
1.  データ ソースに接続します。  
  
     詳細については、「[データ ソースへの接続](../../../docs/framework/data/adonet/connecting-to-a-data-source.md)」を参照してください。  
  
2.  フォームでコントロールを選択し、\[プロパティ\] ウィンドウを開きます。  
  
3.  \[**\(DataBindings\)**\] プロパティを展開し、\[**\(詳細\)**\] ボックスの省略記号ボタン \(![VisualStudioEllipsesButton スクリーンショット](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")\) をクリックして、\[**フォーマットと詳細バインド**\] ダイアログ ボックスを表示します。このダイアログ ボックスには、そのコントロールのすべてのプロパティの一覧が表示されます。  
  
4.  バインドするプロパティを選択し、\[**バインド**\] の矢印をクリックします。  
  
     使用できるデータ ソースの一覧が表示されます。  
  
5.  目的の 1 つのデータ要素が見つかるまで、バインド先のデータ ソースを展開します。  
  
     たとえば、データセットのテーブル内の列の値にバインドする場合は、データセットの名前を展開し、次にテーブル名を展開して、列名を表示します。  
  
6.  バインド先の要素の名前をクリックします。  
  
7.  \[**形式の種類**\] ボックスで、コントロールに表示されるデータに適用する形式をクリックします。  
  
     どの形式でも、データ ソースに <xref:System.DBNull> が含まれている場合には、コントロールに表示する値を指定できます。  それ以外の場合、オプションは、選択する形式の種類に応じて多少変わります。  次の表に、形式の種類とオプションを示します。  
  
    |形式の種類|書式設定のオプション|  
    |-----------|----------------|  
    |書式設定なし|オプションはありません。|  
    |数字|**\[小数点以下の桁数\]** アップダウン コントロールを使用して小数点以下の桁数を指定します。|  
    |通貨|**\[小数点以下の桁数\]** アップダウン コントロールを使用して小数点以下の桁数を指定します。|  
    |日付と時刻|**\[種類\]** 選択ボックス内の項目のいずれかを選択して、日付と時刻の表示方法を選択します。|  
    |指数|**\[小数点以下の桁数\]** アップダウン コントロールを使用して小数点以下の桁数を指定します。|  
    |カスタム|カスタム書式指定文字列を使用するように指定します。<br /><br /> 詳細については、「[型の書式設定](../../../docs/standard/base-types/formatting-types.md)」を参照してください。 **Note:**  カスタム書式指定文字列を使用した場合、データ ソースとバインド コントロールの間を往復したときにデータが正常に維持される保証はありません  その代わりに、バインディングで <xref:System.Windows.Forms.Binding.Parse> イベントまたは <xref:System.Windows.Forms.Binding.Format> イベントを処理し、イベント処理コードでカスタム書式を適用します。|  
  
8.  \[**OK**\] をクリックして \[**フォーマットと詳細バインド**\] ダイアログ ボックスを閉じ、\[プロパティ\] ウィンドウに戻ります。  
  
## 参照  
 [方法 : Windows フォームに単純バインド コントロールを作成する](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)   
 [Windows フォームでのユーザー入力の検証](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)   
 [Windows フォームでのデータ バインド](../../../docs/framework/winforms/windows-forms-data-binding.md)