---
title: '方法 : MDI アプリケーションでメニューの自動マージを設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- Merging [Windows Forms], automatic menu
ms.assetid: 55e32cad-1141-4a56-aa33-d9543ca3d393
ms.openlocfilehash: e308ef8327fc439f52c4e3476a663f47fa00a379
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33533462"
---
# <a name="how-to-set-up-automatic-menu-merging-for-mdi-applications"></a>方法 : MDI アプリケーションでメニューの自動マージを設定する
次の手順でマルチ ドキュメント インターフェイス (MDI) アプリケーション内の自動マージを設定するための基本的な手順は、<xref:System.Windows.Forms.MenuStrip>です。  
  
### <a name="to-set-up-automatic-menu-merging"></a>メニューの自動マージを設定するには  
  
1.  設定して、MDI 親フォームを作成、<xref:System.Windows.Forms.Form.IsMdiContainer%2A>プロパティを`true`です。  
  
2.  追加、 <xref:System.Windows.Forms.MenuStrip> MDI 親の設定をその<xref:System.Windows.Forms.Form.MainMenuStrip%2A>にプロパティ<xref:System.Windows.Forms.MenuStrip>です。  
  
3.  MDI 子フォームを作成し、設定、<xref:System.Windows.Forms.Form.MdiParent%2A>プロパティを親フォームの名前にします。  
  
4.  追加、 <xref:System.Windows.Forms.MenuStrip> MDI 子フォームにします。  
  
5.  子フォームで、設定、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>のプロパティ、<xref:System.Windows.Forms.MenuStrip>に`false`です。  
  
6.  メニュー項目に子フォームの追加<xref:System.Windows.Forms.MenuStrip>親フォームのマージする<xref:System.Windows.Forms.MenuStrip>子フォームがアクティブになったとき。  
  
7.  使用して、<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A>子フォームの 項目をメニューのプロパティ<xref:System.Windows.Forms.MenuStrip>を親フォームにマージする方法を制御します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
