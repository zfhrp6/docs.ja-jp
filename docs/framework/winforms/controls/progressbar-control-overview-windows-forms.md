---
title: ProgressBar コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- ProgressBar
helpviewer_keywords:
- ProgressBar control [Windows Forms], about ProgressBar control
- progress controls [Windows Forms], about progress controls
ms.assetid: a05d9cba-3a6a-4f8f-94b8-8ec12799fb80
ms.openlocfilehash: bd2b9615b0061a8f2133229edb49357cde69b39e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539430"
---
# <a name="progressbar-control-overview-windows-forms"></a>ProgressBar コントロールの概要 (Windows フォーム)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.ToolStripProgressBar> コントロールは、<xref:System.Windows.Forms.ProgressBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.ProgressBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 Windows フォーム<xref:System.Windows.Forms.ProgressBar>コントロールが水平のバーに配置された四角形の適切な数を表示することによって、プロセスの進行状況を示します。 プロセスが完了すると、バーが入力されます。 進行状況バーが方法の概要を把握するためによく使用されるまで、プロセスを完了するまでの待機時間たとえば、ときにサイズの大きなファイルが読み込まれています。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ProgressBar>コントロールがフォームに水平方向でのみことができます。  
  
## <a name="key-properties-and-methods"></a>キー プロパティとメソッド  
 キー プロパティ、<xref:System.Windows.Forms.ProgressBar>コントロールは<xref:System.Windows.Forms.ProgressBar.Value%2A>、 <xref:System.Windows.Forms.ProgressBar.Minimum%2A>、および<xref:System.Windows.Forms.ProgressBar.Maximum%2A>です。 <xref:System.Windows.Forms.ProgressBar.Minimum%2A>と<xref:System.Windows.Forms.ProgressBar.Maximum%2A>プロパティが、進行状況バーが表示できる最大と最小値を設定します。 <xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティが行われた操作の完了に向けた進行状況を表します。 値がによって表示される、コントロールに表示されるバーがブロックで構成されるため、<xref:System.Windows.Forms.ProgressBar>コントロールのみ概算するための<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティの現在の値。 サイズに基づいて、<xref:System.Windows.Forms.ProgressBar>コントロール、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティには、次のブロックを表示するタイミングを決定します。  
  
 現在の進行状況の値を更新する最も一般的な方法を設定するコードを記述する、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティです。 サイズの大きなファイルの読み込みの例では、キロバイト単位でファイルのサイズを最大値を設定する可能性があります。 などの場合、<xref:System.Windows.Forms.ProgressBar.Maximum%2A>プロパティが 100 に設定、<xref:System.Windows.Forms.ProgressBar.Minimum%2A>プロパティが 10 に設定と<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティが設定されて 50 に 5 つの四角形が表示されます。 これは、表示可能な数の半分です。  
  
 ただし、他の方法で表示される値を変更するのには、<xref:System.Windows.Forms.ProgressBar>設定とは別のコントロール、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティを直接です。 <xref:System.Windows.Forms.ProgressBar.Step%2A>をインクリメントする値を指定するプロパティを使用することができます、<xref:System.Windows.Forms.ProgressBar.Value%2A>によってプロパティです。 呼び出すことで、<xref:System.Windows.Forms.ProgressBar.PerformStep%2A>メソッドには、値が 1 ずつ増分されます。 増分値を変更するには、使用することができます、<xref:System.Windows.Forms.ProgressBar.Increment%2A>メソッドを増分する値を指定し、<xref:System.Windows.Forms.ProgressBar.Value%2A>プロパティです。  
  
 現在の操作について、ユーザーに通知してグラフィカルに表示する別のコントロールは、<xref:System.Windows.Forms.StatusBar>コントロール。  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip>と<xref:System.Windows.Forms.ToolStripStatusLabel>コントロールの置換し、する機能を追加、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>コントロールですただし、、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>場合、旧バージョンとの互換性と将来の使用の両方のコントロールが保持されますします。選択します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ProgressBar>  
 [ProgressBar コントロール](../../../../docs/framework/winforms/controls/progressbar-control-windows-forms.md)
