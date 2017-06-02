---
title: "方法 : Windows フォームの ToolTip コンポーネントの遅延時間を変更する | Microsoft Docs"
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
  - "例 [Windows フォーム], ツールヒント"
  - "ToolTip コンポーネント [Windows フォーム], 遅延時間の値"
  - "ツールヒント [Windows フォーム], 遅延時間の値"
ms.assetid: 08979ba7-dd84-477b-ab17-8d06e759be99
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : Windows フォームの ToolTip コンポーネントの遅延時間を変更する
Windows フォームの <xref:System.Windows.Forms.ToolTip> コンポーネントには、遅延時間を設定するプロパティが複数あります。  これらのプロパティの単位はすべてミリ秒です。  <xref:System.Windows.Forms.ToolTip.InitialDelay%2A> プロパティは、ツールヒント文字列が表示されるまでにユーザーがコントロールをポイントし続ける時間を決定します。  <xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> プロパティは、1 つのコントロールから別のコントロールにマウスを移動したときに次のツールヒント文字列が表示されるまでにかかる時間を、ミリ秒単位で設定します。  <xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> プロパティは、ツールヒント文字列が表示されている時間の長さを決定します。  これらの値は個別に設定したり、<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> プロパティの値で設定したりできます。他の遅延時間プロパティは、<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> に割り当てた値に基づいて設定されます。  たとえば、<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> の値を N に設定した場合、<xref:System.Windows.Forms.ToolTip.InitialDelay%2A> は N に、<xref:System.Windows.Forms.ToolTip.ReshowDelay%2A> は <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> の値を 5 で割った値 \(N\/5\) に、<xref:System.Windows.Forms.ToolTip.AutoPopDelay%2A> は <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A> プロパティの値に 5 を掛けた値 \(5N\) に設定されます。  
  
### 遅延時間を設定するには  
  
1.  次の例に示すように、各プロパティを設定します。  
  
    ```vb  
    ToolTip1.InitialDelay = 500  
    ToolTip1.ReshowDelay = 100  
    ToolTip1.AutoPopDelay = 5000  
  
    ```  
  
    ```csharp  
    ToolTip1.InitialDelay = 500;  
    ToolTip1.ReshowDelay = 100;  
    ToolTip1.AutoPopDelay = 5000;  
  
    ```  
  
    ```cpp  
    toolTip1->InitialDelay = 500;  
    toolTip1->ReshowDelay = 100;  
    toolTip1->AutoPopDelay = 5000;  
    ```  
  
## 参照  
 [ToolTip コンポーネントの概要](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md)   
 [方法 : デザイン時に Windows フォームのコントロールにツールヒントを設定する](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)   
 [ToolTip コンポーネント](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md)