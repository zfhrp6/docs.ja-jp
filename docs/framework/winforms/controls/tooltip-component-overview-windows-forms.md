---
title: "ToolTip コンポーネントの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff2364b5c7223c265571257920a7c7e794b4921b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-component-overview-windows-forms"></a>ToolTip コンポーネントの概要 (Windows フォーム)
Windows フォーム <xref:System.Windows.Forms.ToolTip> コンポーネントは、ユーザーがコントロールをポイントしたときにテキストを表示します。 ツールヒントは任意のコントロールに関連付けることができます。 このコンポーネントの使用例: フォームの容量を節約するボタンに小さなアイコンを表示し、ボタンの機能を説明するツールヒントを使用します。  
  
## <a name="working-with-the-tooltip-component"></a>ToolTip コンポーネントの操作  
 A<xref:System.Windows.Forms.ToolTip>コンポーネントは、提供、`ToolTip`プロパティを複数のコントロール Windows フォームまたはその他のコンテナーです。 たとえば、1 つ配置した場合<xref:System.Windows.Forms.ToolTip>フォームのコンポーネントは、「の名前を入力」表示できる、<xref:System.Windows.Forms.TextBox>を制御し、「ここをクリックして変更を保存する」、<xref:System.Windows.Forms.Button>コントロール。  
  
 主要なメソッド、<xref:System.Windows.Forms.ToolTip>コンポーネントは<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>と<xref:System.Windows.Forms.ToolTip.GetToolTip%2A>です。 使用することができます、<xref:System.Windows.Forms.ToolTip.SetToolTip%2A>コントロールに対して表示されるツールヒントを設定します。 詳細については、次を参照してください。[する方法: デザイン時に Windows フォームのコントロールにツールヒントを設定](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)です。 プロパティは<xref:System.Windows.Forms.ToolTip.Active%2A>設定する必要があります`true`が表示されるツールヒントのおよび<xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>、ツール ヒントの文字列が表示されている時間の長さを設定する、ユーザーが表示されるツールヒントのコントロールでポイントする必要があります期間と長時間かかる場合は、方法表示されるツールヒント ウィンドウを取得します。 詳細については、次を参照してください。[する方法: Windows フォームの ToolTip コンポーネントの遅延時間を変更](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolTip>  
 [方法: デザイン時に Windows フォームのコントロールにツールヒントを設定する](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [方法: Windows フォームの ToolTip コンポーネントの遅延時間を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)
