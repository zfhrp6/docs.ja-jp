---
title: TableLayoutPanel コントロールの推奨される手順
ms.date: 03/30/2017
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
ms.openlocfilehash: 40322dc6c5facd4167a4c9ac5c12fdf2a8831b7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526454"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a>TableLayoutPanel コントロールの推奨される手順
<xref:System.Windows.Forms.TableLayoutPanel>コントロールは、Windows フォームで使用する前に慎重に考慮すべき強力なレイアウト機能を提供します。  
  
## <a name="recommendations"></a>推奨事項  
 次の推奨事項は、使用するのに役立つ、<xref:System.Windows.Forms.TableLayoutPanel>最大限に活用するコントロール。  
  
### <a name="targeted-use"></a>対象の使用  
 使用して、<xref:System.Windows.Forms.TableLayoutPanel>慎重を制御します。 サイズ変更可能なレイアウトを必要とするすべての状況で使用する必要がありますされません。 次のリストの使用を最大限に活用するレイアウトの説明、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。  
  
-   保存されているフォームの相互に比例してサイズが変更される複数の部分のレイアウトです。  
  
-   変更または追加、または削除、ユーザーがカスタマイズできるフィールドを持つデータ エントリ フォームなどの実行時に動的に生成されるレイアウトは、基本設定に基づいています。  
  
-   レイアウトを全体の固定サイズのままにします。 たとえば、800 x 600 よりも小さい必要のあるダイアログ ボックスがありますが、ローカライズされた文字列をサポートする必要があります。  
  
 次のように、有効ではありませんが大幅に使用するレイアウト、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。  
  
-   単純なデータ エントリ フォームを 1 つの列のラベルとテキスト入力領域の 1 つの列です。  
  
-   1 つの大きなフォームは、サイズ変更が発生したときに使用可能なすべての領域の塗りつぶし領域を表示します。 この例は、1 つを表示するフォーム<xref:System.Windows.Forms.PropertyGrid>コントロール。 この例を使用して固定、フォームのサイズが変更されるときにそれ以外のものを展開するためです。  
  
 内にある必要があるコントロールを慎重に選択して、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 アンカーを使用して、30% ずつ増加して、文字列を使っている場合は、使用を検討して、<xref:System.Windows.Forms.Control.Anchor%2A>プロパティのみです。 場合は、レイアウトに必要な領域を見積もるを使用して<xref:System.Windows.Forms.Control.Dock%2A>と<xref:System.Windows.Forms.Control.Anchor%2A>残りの領域の詳細の見積もりよりも簡単です、<xref:System.Windows.Forms.Control.AutoSize%2A>動作します。  
  
 一般を使用してレイアウトを設計するとき、<xref:System.Windows.Forms.TableLayoutPanel>制御、できるだけ単純な設計を保持します。  
  
### <a name="use-the-document-outline-window"></a>ドキュメント アウトライン ウィンドウを使用します。  
 ドキュメント アウトライン ウィンドウでは、コントロールの z オーダーと、親子のリレーションシップを操作に使用できるのレイアウトのツリー ビューを示します。 **表示 メニュー****その他のウィンドウ**選択してから、 **ドキュメント アウトライン**です。  
  
### <a name="avoid-nesting"></a>入れ子を回避します。  
 その他の入れ子を避ける<xref:System.Windows.Forms.TableLayoutPanel>内で制御、<xref:System.Windows.Forms.TableLayoutPanel>コントロール。 入れ子になったレイアウトのデバッグは難しくなります。  
  
### <a name="avoid-visual-inheritance"></a>ビジュアル継承を避ける  
 <xref:System.Windows.Forms.TableLayoutPanel>コントロールは、Windows フォーム デザイナーでのビジュアル継承をサポートしません。 A <xref:System.Windows.Forms.TableLayoutPanel> 「ロックされている」デザイン時に、派生クラスでのコントロールが表示されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
