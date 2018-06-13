---
title: Windows フォームの MenuStrip コントロールへのメニュー項目のマージ
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
ms.openlocfilehash: 2782ae483d673f8f1eccab10876aca858737260a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539790"
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>Windows フォームの MenuStrip コントロールへのメニュー項目のマージ
マルチ ドキュメント インターフェイス (MDI) アプリケーションがある場合は、親フォームのメニューにメニュー項目や子フォーム全体のメニューをマージできます。  
  
 このトピックでは、MDI アプリケーションでメニュー項目のマージに関連付けられている基本的な概念について説明します。  
  
## <a name="general-concepts"></a>一般的な概念  
 マージ手順には、ターゲットとソース管理の両方が含まれます。  
  
-   ターゲットが、<xref:System.Windows.Forms.MenuStrip>メニュー項目のマージをメインまたは MDI 親フォームのコントロールです。  
  
-   ソースは、<xref:System.Windows.Forms.MenuStrip>ターゲット メニューにマージするメニュー項目を含む MDI 子フォーム上のコントロールです。  
  
 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>プロパティは、現在の MDI のタイトルが表示されます - ドロップダウン リストを持つ親フォームの MDI 子メニュー項目を識別します。 たとえば、通常を一覧表示する MDI 子フォームで現在開かれている、**ウィンドウ**メニュー。  
  
 <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A>プロパティを識別するメニュー項目に由来する<xref:System.Windows.Forms.MenuStrip>MDI 子フォームでします。  
  
 メニュー項目は、手動または自動マージできます。 メニュー項目が、両方の方法に対して同じ方法でマージが、マージが「手動マージ」と「の自動マージ」セクションでは、このトピックの後半で説明したように、異なるアクティブ化します。 手動および自動マージするには、各マージ アクションは、次のマージ処理の影響を与えます。  
  
 <xref:System.Windows.Forms.MenuStrip> 1 つからメニュー項目を移動するマージ<xref:System.Windows.Forms.ToolStrip>を別の場合と同様に、それらを複製するのではなく<xref:System.Windows.Forms.MainMenu>です。  
  
## <a name="mergeaction-values"></a>MergeAction 値  
 ソース内のメニュー項目にマージ アクションを設定する<xref:System.Windows.Forms.MenuStrip>を使用して、<xref:System.Windows.Forms.MergeAction>プロパティです。  
  
 次の表では、使用できるマージ処理の意味と一般的な使用について説明します。  
  
|MergeAction 値|説明|一般的な用途|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|(既定値)ソース項目をターゲット項目のコレクションの末尾に追加します。|プログラムの一部がアクティブな場合、メニューの末尾にメニュー項目を追加します。|  
|<xref:System.Windows.Forms.MergeAction.Insert>|指定された場所で、ターゲット項目のコレクションに元の項目を追加、<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>ソース項目のプロパティで設定します。|プログラムの一部がアクティブになったときに、中央またはメニューの先頭にメニュー項目を追加します。<br /><br /> 場合の値<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>は両方のメニュー項目を追加する逆の順序で。 設定<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>適切に元の順序を保持します。|  
|<xref:System.Windows.Forms.MergeAction.Replace>|一致するテキストを検索または使用して、<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>以外の場合、テキストの不一致が検出され、ソースのメニュー項目に一致する対象のメニュー項目を置換値します。|何か異なるものと同じ名前のソースのメニュー項目にターゲット メニュー項目を置き換えます。|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|一致するテキストを検索または使用して、<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>値の場合は、テキストの不一致が検出され、ソースからすべてのドロップダウン項目をターゲットに追加します。|メニュー構造を構築を挿入します。 または、サブメニューにメニュー項目を追加またはサブメニューからメニュー項目を削除します。 主に、MDI 子からメニュー項目を追加するなど、 <xref:System.Windows.Forms.MenuStrip>**名前を付けて保存**メニュー。<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly> 使用すると、操作を行わずにメニュー構造をナビゲートできます。 それ以降の項目を評価する方法を提供します。|  
|<xref:System.Windows.Forms.MergeAction.Remove>|一致するテキストを検索または使用して、<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>値の場合は、テキストの不一致が検出され、ターゲットから項目を削除します。|ターゲットからメニュー項目を削除する<xref:System.Windows.Forms.MenuStrip>です。|  
  
## <a name="manual-merging"></a>手動マージ  
 のみ<xref:System.Windows.Forms.MenuStrip>のコントロールの自動マージに参加します。 など、他のコントロールの項目を結合する<xref:System.Windows.Forms.ToolStrip>と<xref:System.Windows.Forms.StatusStrip>コントロール、する必要があります手動でマージを呼び出すことによって、<xref:System.Windows.Forms.ToolStripManager.Merge%2A>と<xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A>必要に応じて、コード内のメソッドです。  
  
## <a name="automatic-merging"></a>自動マージ  
 ソース フォームをアクティブ化して、MDI アプリケーションの自動マージを使用することができます。 使用する、 <xref:System.Windows.Forms.MenuStrip> MDI アプリケーションでは、次のように設定します。、<xref:System.Windows.Forms.Form.MainMenuStrip%2A>プロパティをターゲットに<xref:System.Windows.Forms.MenuStrip>アクションの結合ソースで行うように<xref:System.Windows.Forms.MenuStrip>はターゲットに反映されます<xref:System.Windows.Forms.MenuStrip>です。  
  
 アクティブ化して自動マージをトリガーすることができます、 <xref:System.Windows.Forms.MenuStrip> MDI ソースにします。 ソースの起動時に<xref:System.Windows.Forms.MenuStrip>MDI ターゲットにマージされます。 新しいフォームがアクティブになったときに、マージで最後のフォームの元に戻す、新しいフォームに発生します。 設定してこの動作を制御することができます、<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A>プロパティごとに、必要に応じて<xref:System.Windows.Forms.ToolStripItem>を設定したり、<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>プロパティをそれぞれ<xref:System.Windows.Forms.MenuStrip>です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.MenuStrip>  
 [MenuStrip コントロール](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [方法: MenuStrip を使用して MDI ウィンドウの一覧を作成する](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)  
 [方法: MDI アプリケーションでメニューの自動マージを設定する](../../../../docs/framework/winforms/controls/how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
