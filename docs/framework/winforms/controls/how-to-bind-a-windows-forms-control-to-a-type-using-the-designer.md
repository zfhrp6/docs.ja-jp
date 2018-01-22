---
title: "方法 : デザイナーを使って Windows フォーム コントロールを型にバインドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee932e7cb4a3333ac56242e281ec64d3016746f9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>方法 : デザイナーを使って Windows フォーム コントロールを型にバインドする
データをやり取りするコントロールを作成する際、オブジェクトではなく型にコントロールをバインドすることが必要な場合があります。 データを使用できないが、データ バインド コントロールで型のパブリック インターフェイスからデータを表示する必要がある場合、通常はデザイン時にコントロールを型にバインドする必要があります。 次の手順を新規作成する方法を説明する<xref:System.Windows.Forms.BindingSource>されている型にバインドし、型のプロパティのいずれかにバインドする方法、<xref:System.Windows.Forms.TextBox.Text%2A>のプロパティ、<xref:System.Windows.Forms.TextBox>です。  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a>BindingSource を型にバインドするには  
  
1.  Windows フォーム プロジェクトを作成します。  
  
     詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  **デザイン**ビューで、ドラッグ、<xref:System.Windows.Forms.BindingSource>コンポーネントをフォームにします。  
  
3.  **プロパティ**ウィンドウで、矢印をクリックして、<xref:System.Windows.Forms.BindingSource.DataSource%2A>プロパティです。  
  
4.  **DataSource UI 型エディター**で、**[プロジェクト データ ソースの追加]** をクリックします。  
  
5.  **[データ ソースの種類を選択]** ページで、**[オブジェクト]** を選択して **[次へ]** をクリックします。  
  
6.  バインド先となる型を選択します。  
  
    -   バインド先となる型が現在のプロジェクトにある場合、または、型を含むアセンブリが参照として既に追加されている場合は、ノードを展開し、目的の型を探して選択します。  
  
         - または -  
  
    -   バインド先となる型が、現在、参照の一覧にはなく、別のアセンブリにある場合は、**[参照の追加]** をクリックして **[プロジェクト]** タブをクリックします。目的のビジネス オブジェクトを含むプロジェクトを選択して **[OK]** をクリックします。 このプロジェクトは、アセンブリの一覧に表示されるため、ノードを展開し、目的の型を探して選択します。  
  
        > [!NOTE]
        >  フレームワークまたは Microsoft アセンブリの型にバインドする場合は、**[Microsoft または System で始まるアセンブリを表示しない]** チェックボックスをオフにします。  
  
7.  **[次へ]**をクリックし、 **[完了]**をクリックします。  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a>コントロールを BindingSource にバインドするには  
  
1.  フォームに <xref:System.Windows.Forms.TextBox> を追加します。  
  
2.  **[プロパティ]** ウィンドウで **(DataBindings)** ノードを展開します。  
  
3.  矢印をクリックして、次に、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティです。  
  
4.  **データ ソースの UI 型エディター**、ノードを展開します、<xref:System.Windows.Forms.BindingSource>以前は、追加され、プロパティにバインドするバインドの種類の選択、<xref:System.Windows.Forms.TextBox.Text%2A>のプロパティ、<xref:System.Windows.Forms.TextBox>です。  
  
## <a name="see-also"></a>参照  
 [BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [方法: Windows フォーム コントロールを型にバインドする](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 [Visual Studio でのデータへのコントロールのバインド](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
