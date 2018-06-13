---
title: DataRepeater コントロールの概要 (Visual Studio)
ms.date: 07/20/2015
helpviewer_keywords:
- repeating data
- DataRepeater, overview
- DataRepeater
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
ms.openlocfilehash: fc0cf9c358faf3e738eb3b24ec61577b88dbce4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591951"
---
# <a name="introduction-to-the-datarepeater-control-visual-studio"></a>DataRepeater コントロールの概要 (Visual Studio)
Visual Basic Power Packs の <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> コントロールは、データベース テーブルの行などの繰り返されるデータを表示するコントロールの、スクロール可能なコンテナーです。 データのレイアウトを詳細に制御する必要がある場合は、 <xref:System.Windows.Forms.DataGridView> コントロールの代わりにこのコントロールを使用できます。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 「グループを繰り返し実行」関連するコントロールのスクロールのビューで複数のインスタンスを作成しています。 これにより、ユーザーを同時に複数のレコードを表示できます。  
  
## <a name="overview"></a>概要  
 デザイン時に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>制御は、2 つのセクションで構成されます。 外部セクションは、*ビューポート*、スクロール可能なデータが実行時に表示されます。 呼ばれる内部の (上部) セクション、*項目テンプレート*は、通常 1 つのコントロール、データ ソースのフィールドごとに、実行時に繰り返されるコントロールを配置します。 プロパティと項目テンプレートのコントロールにカプセル化されて、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>プロパティです。  
  
 実行時に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>はバーチャル マシンにコピー<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>データを表示する、各レコードはビューにスクロールするときに使用されるオブジェクト。 内の個々 のレコードの表示をカスタマイズすることができます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>イベントなどが含まれている値に基づいて、フィールドを強調表示します。 詳細については、次を参照してください。[する方法: DataRepeater コントロールの外観を変更](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)です。  
  
 最も一般的な使用、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールは、データベース テーブルまたはその他のバインドされたデータ ソースからデータを表示します。 加え[!INCLUDE[vstecado](~/includes/vstecado-md.md)]データ オブジェクト、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールを実装する任意のクラスにバインドできます、<xref:System.Collections.IList>インターフェイス (配列を含む)、実装するクラス、<xref:System.ComponentModel.IListSource>インターフェイスを実装するクラス、 <xref:System.ComponentModel.IBindingList>インターフェイス、または任意のクラスを実装する、<xref:System.ComponentModel.IBindingListView>インターフェイスです。  
  
### <a name="data-binding"></a>データ バインディング  
 通常からフィールドをドラッグしてデータ バインディングを行う、**データソース** ウィンドウ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。 詳細については、次を参照してください。[する方法: DataRepeater コントロールにバインドされているデータを表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)です。  
  
 大量のデータを扱う場合は、設定、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>プロパティを`True`を利用できるデータのサブセットを表示します。 仮想モードには、元のデータ キャッシュの実装が必要です、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>が作成されますが、実行時にデータ キャッシュを使用してすべてのやり取りを制御する必要があります。 詳細については、次を参照してください。 [DataRepeater コントロールでの仮想モード](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md)です。  
  
 バインドされていないコントロールを表示することも、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール。 たとえば、項目ごとに繰り返されるイメージを表示できます。 詳細については、次を参照してください。[する方法: DataRepeater コントロールにバインドされていないコントロールを表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)です。  
  
### <a name="events"></a>イベント  
 最も重要なイベント、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールは、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>ビューに新しい項目がスクロールされたときに発生するイベントと<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>項目が選択されているときに発生するイベントです。 使用することができます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>アイテムの外観を変更するイベントです。 たとえば、負の値を強調表示することができます。 使用して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>項目が選択されているときにコントロールの値にアクセスするイベントです。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールは、コード エディターですべて標準のコントロールのイベントを公開します。 ただし、一部のイベントは使用できません。 キーボードし、マウス イベントをなど`KeyDown`、 `Click`、および`MouseDown`は発生しません。 実行時にあるため、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール自体がフォーカスを持つことはありません。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>実行時にのみに作成されるため、デザイン時にイベントを公開しませんしません。 キーボードとマウスのイベントを処理するかどうかは、ことができますを追加する、<xref:System.Windows.Forms.Panel>コントロールを<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>でのイベントを処理し、デザイン時と、<xref:System.Windows.Forms.Panel>です。 詳細については、次を参照してください。 [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)です。  
  
### <a name="customizations"></a>カスタマイズ  
 動作と外観をカスタマイズする方法はたくさんあります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>実行時およびデザイン時の両方を制御します。 色を変更する、非表示または項目ヘッダーを変更、方向を変更する水平方向に垂直方向、多くのプロパティを設定できます。 詳細については、次を参照してください[する方法: DataRepeater コントロールの外観を変更](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)、[する方法: DataRepeater コントロールに項目ヘッダーを表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)、と[する方法: のレイアウトを変更する。DataRepeater コントロール](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)です。  
  
 注一部のプロパティに適用される、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール自体にのみ適用されるものは、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>です。 プロパティを設定する前に、コントロールの適切な部分があることを確認します。 詳細については、次を参照してください。[する方法: DataRepeater コントロールの外観を変更](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)です。  
  
 その他のカスタマイズには、レコード追加または削除する機能を制御する、検索機能の追加、およびマスター/詳細形式で関連データの表示が含まれます。 詳細については、次を参照してください[する方法: DataRepeater の項目の削除の追加を無効にすると](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)、[する方法: DataRepeater コントロールでデータを検索](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)、および[する方法: 2 つを使用してマスター/詳細フォームを作成する。DataRepeater コントロール (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)です。  
  
## <a name="see-also"></a>関連項目  
 [DataRepeater コントロール](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)  
 [チュートリアル: DataRepeater コントロールでのデータの表示](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)  
 [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
