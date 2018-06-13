---
title: LinkLabel コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
ms.openlocfilehash: 40326a9055ff51efae5f4c64744d0966870c6f6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535013"
---
# <a name="linklabel-control-overview-windows-forms"></a>LinkLabel コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.LinkLabel>コントロールでは、Windows フォーム アプリケーションに Web スタイルのリンクを追加することができます。 使用することができます、<xref:System.Windows.Forms.LinkLabel>使用できるすべてのコントロール、<xref:System.Windows.Forms.Label>の制御。 設定することもできる、テキストの一部としてファイル、フォルダー、または Web ページへのリンク。  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a>LinkLabel コントロールで行うことができます。  
 すべてのプロパティ、メソッド、およびのイベントだけでなく、<xref:System.Windows.Forms.Label>コントロール、<xref:System.Windows.Forms.LinkLabel>コントロール ハイパーリンクおよびリンクの色のプロパティがあります。 <xref:System.Windows.Forms.LinkLabel.LinkArea%2A>プロパティは、リンクをアクティブにするテキストの領域を設定します。 <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>、 <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>、および<xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A>プロパティは、リンクの色を設定します。 <xref:System.Windows.Forms.LinkLabel.LinkClicked>イベントは、このリンク テキストが選択されているときの動作を決定します。  
  
 最も簡単な使い方、<xref:System.Windows.Forms.LinkLabel>コントロールを使用して、1 つのリンクを表示する、<xref:System.Windows.Forms.LinkLabel.LinkArea%2A>プロパティもハイパーリンクを表示できる複数を使用して、<xref:System.Windows.Forms.LinkLabel.Links%2A>プロパティです。 <xref:System.Windows.Forms.LinkLabel.Links%2A>プロパティでは、リンクのコレクションにアクセスすることができます。 内のデータを指定することも、<xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A>プロパティをそれぞれ個別<xref:System.Windows.Forms.LinkLabel.Link>オブジェクト。 値、<xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A>を表示するファイルの場所または Web サイトのアドレスを格納するプロパティを使用できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.LinkLabel>  
 [Label コントロールの概要](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [方法: Windows フォーム LinkLabel コントロールでオブジェクトまたは Web ページにリンクする](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [方法: Windows フォーム LinkLabel コントロールの表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
