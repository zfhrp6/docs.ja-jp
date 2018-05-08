---
title: AutoSize プロパティの概要
ms.date: 03/30/2017
helpviewer_keywords:
- sizing [Windows Forms], automatic
- layout [Windows Forms], AutoSize
- automatic sizing
- AutoSizeMode property
ms.assetid: 62fd82a2-9565-4f65-925b-9d1e66dc4e7d
ms.openlocfilehash: d7502d11c6cad526c5b19ea2d98e39756d518b98
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="autosize-property-overview"></a>AutoSize プロパティの概要
<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティで指定された値を実現するために必要な場合は、そのサイズを変更するコントロールを使用して、<xref:System.Windows.Forms.Control.PreferredSize%2A>プロパティです。 設定して特定のコントロールのサイズ変更動作を調整する、`AutoSizeMode`プロパティです。  
  
## <a name="autosize-behavior"></a>AutoSize 動作  
 一部のコントロールのみをサポート、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティです。 さらに、一部のコントロールをサポートする、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティをサポートしても、`AutoSizeMode`プロパティです。  
  
 <xref:System.Windows.Forms.Control.AutoSize%2A>プロパティには、特定のコントロール型との値に応じて、若干異なる動作が生成されます、`AutoSizeMode`プロパティが存在する場合は、プロパティです。 次の表は、常に有効な動作について説明し、それぞれの簡単な説明。  
  
|常に真の動作|説明|  
|--------------------------|-----------------|  
|自動サイズ変更は、ランタイムの機能です。|これは、ことを意味しない拡張またはコントロールを縮小それ以上の効果がありません。|  
|コントロールの値のサイズが変更された場合、<xref:System.Windows.Forms.Control.Location%2A>プロパティは常に定数です。|コントロールの内容が拡大、右方向と下方向が拡張コントロールが表示されます。 コントロールは、左側には拡張されません。|  
|<xref:System.Windows.Forms.Control.Dock%2A>と<xref:System.Windows.Forms.Control.Anchor%2A>プロパティがいつ受け入れられます<xref:System.Windows.Forms.Control.AutoSize%2A>は`true`します。|コントロールの値<xref:System.Windows.Forms.Control.Location%2A>プロパティは、適切な値に調整します。<br /><br /> **注**、<xref:System.Windows.Forms.Label>コントロールは、この規則の例外。 ドッキングされた状態の値を設定すると<xref:System.Windows.Forms.Label>コントロールの<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティを`true`、<xref:System.Windows.Forms.Label>コントロールは伸縮しません。|  
|コントロールの<xref:System.Windows.Forms.Control.MaximumSize%2A>と<xref:System.Windows.Forms.Control.MinimumSize%2A>プロパティは常に受け入れの値に関係なくその<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティです。|<xref:System.Windows.Forms.Control.MaximumSize%2A>と<xref:System.Windows.Forms.Control.MinimumSize%2A>プロパティは影響ありません、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティです。|  
|既定で設定される最小サイズはありません。|つまり、下にある圧縮にコントロールが設定されている場合<xref:System.Windows.Forms.Control.AutoSize%2A>内容の値を持たないとその<xref:System.Windows.Forms.Control.Size%2A>プロパティは、0, 0 です。 ここでは、コントロールは、ポイントに圧縮し、すぐに表示されません。|  
|コントロールを実装しない場合、 <xref:System.Windows.Forms.Control.GetPreferredSize%2A> 、メソッド、<xref:System.Windows.Forms.Control.GetPreferredSize%2A>メソッドに割り当てられている最後の値を返します、<xref:System.Windows.Forms.Control.Size%2A>プロパティです。|つまり、その設定<xref:System.Windows.Forms.Control.AutoSize%2A>に`true`効果はありません。|  
|内のコントロール、<xref:System.Windows.Forms.TableLayoutPanel>セルになるまで、セルに合わせて縮小では常にその<xref:System.Windows.Forms.Control.MinimumSize%2A>に到達します。|このサイズは最大サイズとして適用されます。 これには、セルの一部であるときに、大文字と小文字ではありません、<xref:System.Windows.Forms.SizeType.AutoSize>行または列。|  
  
## <a name="autosizemode-property"></a>AutoSizeMode プロパティ  
 `AutoSizeMode`プロパティは既定値より詳細に制御を提供<xref:System.Windows.Forms.Control.AutoSize%2A>動作します。 `AutoSizeMode`プロパティは、どのコントロールに合わせてサイズの内容を指定します。 などの可能性があるのテキスト、<xref:System.Windows.Forms.Button>コントロールまたはコンテナーの子コントロール。  
  
 次の表に、<xref:System.Windows.Forms.AutoSizeMode>各設定を引き起こします設定と動作の説明。  
  
|AutoSizeMode 設定|動作|  
|--------------------------|--------------|  
|GrowAndShrink|コントロールは、拡大またはその内容を使用するように縮小します。<br /><br /> <xref:System.Windows.Forms.Control.MinimumSize%2A>と<xref:System.Windows.Forms.Control.MaximumSize%2A>の現在の値が、値が受け入れられます、<xref:System.Windows.Forms.Control.Size%2A>プロパティは無視されます。<br /><br /> これは、コントロールと同様の動作、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティと いいえ`AutoSizeMode`プロパティです。|  
|GrowOnly|コントロールは、その内容を使用するように必要に応じて拡張しますが、によって指定された値より小さいことは圧縮されません、<xref:System.Windows.Forms.Control.Size%2A>プロパティです。<br /><br /> これは、`AutoSizeMode` の既定値です。|  
  
## <a name="controls-that-support-the-autosize-property"></a>AutoSize プロパティをサポートするコントロール  
 次の表に、サポートするコントロール、<xref:System.Windows.Forms.Control.AutoSize%2A>と`AutoSizeMode`プロパティです。  
  
|AutoSize のサポート|コントロール型|  
|----------------------|------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> サポートされるプロパティです。<br />-`AutoSizeMode`プロパティです。|<xref:System.Windows.Forms.CheckBox><br /><br /> <xref:System.Windows.Forms.DomainUpDown><br /><br /> <xref:System.Windows.Forms.Label><br /><br /> <xref:System.Windows.Forms.LinkLabel><br /><br /> <xref:System.Windows.Forms.MaskedTextBox> (<xref:System.Windows.Forms.TextBox>ベース)<br /><br /> <xref:System.Windows.Forms.NumericUpDown><br /><br /> <xref:System.Windows.Forms.RadioButton><br /><br /> <xref:System.Windows.Forms.TextBox><br /><br /> <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> サポートされるプロパティです。<br />-   `AutoSizeMode` サポートされるプロパティです。|<xref:System.Windows.Forms.Button><br /><br /> <xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.FlowLayoutPanel><br /><br /> <xref:System.Windows.Forms.Form><br /><br /> <xref:System.Windows.Forms.GroupBox><br /><br /> <xref:System.Windows.Forms.Panel><br /><br /> <xref:System.Windows.Forms.TableLayoutPanel>|  
|-<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティです。|<xref:System.Windows.Forms.CheckedListBox><br /><br /> <xref:System.Windows.Forms.ComboBox><br /><br /> <xref:System.Windows.Forms.DataGridView><br /><br /> <xref:System.Windows.Forms.DateTimePicker><br /><br /> <xref:System.Windows.Forms.ListBox><br /><br /> <xref:System.Windows.Forms.ListView><br /><br /> <xref:System.Windows.Forms.MaskedTextBox><br /><br /> <xref:System.Windows.Forms.MonthCalendar><br /><br /> <xref:System.Windows.Forms.ProgressBar><br /><br /> <xref:System.Windows.Forms.PropertyGrid><br /><br /> <xref:System.Windows.Forms.RichTextBox><br /><br /> <xref:System.Windows.Forms.SplitContainer><br /><br /> <xref:System.Windows.Forms.TabControl><br /><br /> <xref:System.Windows.Forms.TabPage><br /><br /> <xref:System.Windows.Forms.TreeView><br /><br /> <xref:System.Windows.Forms.WebBrowser><br /><br /> <xref:System.Windows.Forms.ScrollBar>|  
  
## <a name="autosize-in-the-design-environment"></a>デザイン環境で自動サイズ調整  
 次の表のコントロールのサイズ変更動作、デザイン時の値に基づいてその<xref:System.Windows.Forms.Control.AutoSize%2A>と`AutoSizeMode`プロパティです。  
  
 上書き、<xref:System.Windows.Forms.Design.ControlDesigner.SelectionRules%2A>プロパティを指定されたコントロールがユーザーのサイズ変更可能な状態かどうかを判断します。 次の表に「できない」ことを意味<xref:System.Windows.Forms.Design.SelectionRules.Moveable>のみ、「が」意味<xref:System.Windows.Forms.Design.SelectionRules.AllSizeable>と<xref:System.Windows.Forms.Design.SelectionRules.Moveable>です。  
  
|Autosize プロパティの設定|デザイン時のサイズ変更のジェスチャ|  
|-----------------------|---------------------------------|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-`AutoSizeMode`プロパティです。|ユーザーは、次のコントロールを除く、デザイン時にコントロールのサイズを変更できません。<br /><br /> -   <xref:System.Windows.Forms.TextBox><br />-   <xref:System.Windows.Forms.MaskedTextBox><br />-   <xref:System.Windows.Forms.RichTextBox><br />-   <xref:System.Windows.Forms.TrackBar>|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowAndShrink>|ユーザーは、デザイン時にコントロールのサイズを変更できません。|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `true`<br />-   `AutoSizeMode` = <xref:System.Windows.Forms.AutoSizeMode.GrowOnly>|ユーザーは、デザイン時にコントロールのサイズを変更できます。 ときに、<xref:System.Windows.Forms.Control.Size%2A>プロパティが設定されて、ユーザーは、コントロールのサイズを増加のみ実行できます。|  
|-   <xref:System.Windows.Forms.Control.AutoSize%2A> = `false`、または<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティを非表示にします。|ユーザーは、デザイン時にコントロールのサイズを変更できます。|  
  
> [!NOTE]
>  Windows フォーム デザイナーの影の生産性を最大化する、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティを<xref:System.Windows.Forms.Form>クラスです。 デザイン時に、フォームが動作かのよう、<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティに設定されている`false`その実際の設定に関係なく、します。 実行時に、特別な設備は行われず、および<xref:System.Windows.Forms.Control.AutoSize%2A>プロパティが適用されるプロパティの設定で指定されたとおりです。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Control.AutoSize%2A>  
 <xref:System.Windows.Forms.Control.PreferredSize%2A>  
 <xref:System.Windows.Forms.Control.GetPreferredSize%2A>
