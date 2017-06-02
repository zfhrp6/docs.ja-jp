---
title: "方法 : デザイナーを使って Windows フォーム コントロールを型にバインドする | Microsoft Docs"
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
  - "BindingSource コンポーネント [Windows フォーム], バインド (型への)"
  - "コントロール [Windows フォーム], バインド (型への)"
  - "型 [Windows フォーム], バインド (コントロールを)"
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : デザイナーを使って Windows フォーム コントロールを型にバインドする
データとやり取りするコントロールをビルドする場合、オブジェクトではなく、型にコントロールをバインドしなければならないときがあります。  データを使用できない可能性はあるが、それでもデータ バインド コントロールに型のパブリック インターフェイスからのデータを表示することが必要な場合、通常はデザイン時にコントロールを型にバインドする必要があります。  次の手順は、型にバインドされる新しい <xref:System.Windows.Forms.BindingSource> を作成し、型のプロパティの 1 つを <xref:System.Windows.Forms.TextBox> の <xref:System.Windows.Forms.TextBox.Text%2A> プロパティにバインドする方法を示しています。  
  
### BindingSource を型にバインドするには  
  
1.  Windows フォーム プロジェクトを作成します。  
  
     詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  **デザイン** ビューから、フォームに <xref:System.Windows.Forms.BindingSource> コンポーネントをドラッグします。  
  
3.  **\[プロパティ\]** ウィンドウの <xref:System.Windows.Forms.BindingSource.DataSource%2A> プロパティの矢印をクリックします。  
  
4.  **DataSource UI 型エディター**の **\[プロジェクト データ ソースの追加\]** をクリックします。  
  
5.  **\[データ ソースの種類を選択\]** ページで、**\[オブジェクト\]** を選択し、**\[次へ\]** をクリックします。  
  
6.  バインド先の型を選択します。  
  
    -   バインド先の型が現在のプロジェクトの中にある場合、またはその型を含むアセンブリが既に参照として追加されている場合は、ノードを展開して目的の型を見つけ、選択します。  
  
         または  
  
    -   バインド先の型が別のアセンブリにあり、現在は参照のリストに含まれていない場合は、**\[参照の追加\]** をクリックし、**\[プロジェクト\]** タブをクリックします。  使用するビジネス オブジェクトが含まれるプロジェクトを選択し、**\[OK\]** をクリックします。  このプロジェクトがアセンブリのリストに表示されるので、ノードを展開して目的の型を見つけ、選択できます。  
  
        > [!NOTE]
        >  フレームワークまたは Microsoft アセンブリにある型にバインドする場合は、**\[Microsoft または System で始まるアセンブリを表示しない\]** チェック ボックスをオフにします。  
  
7.  **\[次へ\]** をクリックし、**\[完了\]** をクリックします。  
  
### コントロールを BindingSource にバインドするには  
  
1.  フォームに <xref:System.Windows.Forms.TextBox> を追加します。  
  
2.  **\[プロパティ\]** ウィンドウで **\[\(DataBindings\)\]** ノードを展開します。  
  
3.  <xref:System.Windows.Forms.TextBox.Text%2A> プロパティの横にある矢印をクリックします。  
  
4.  **DataSource UI 型エディター**で、前の手順で追加した <xref:System.Windows.Forms.BindingSource> のノードを展開し、<xref:System.Windows.Forms.TextBox> の <xref:System.Windows.Forms.TextBox.Text%2A> プロパティにバインドする型のプロパティを選択します。  
  
## 参照  
 [BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)   
 [方法 : Windows フォーム コントロールを型にバインドする](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)   
 [Visual Studio でのデータへのコントロールのバインド](../Topic/Bind%20controls%20to%20data%20in%20Visual%20Studio.md)