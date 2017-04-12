---
title: "DataRepeater コントロール (Visual Studio) の概要 |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- repeating data
- DataRepeater, overview
- DataRepeater
ms.assetid: 78a52a1d-65f0-4ecb-97ff-53bc114300c5
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 86078426494caabefc6bbfb036037007e830e1cb
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-the-datarepeater-control-visual-studio"></a>DataRepeater コントロールの概要 (Visual Studio)
Visual Basic Power Packs<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールでは、表示するコントロールを繰り返し、データがデータベース テーブルの行などのスクロール可能なコンテナー</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 。 代わりに使用できる、<xref:System.Windows.Forms.DataGridView>必要がある場合、データのレイアウトを制御する詳細を制御します</xref:System.Windows.Forms.DataGridView>。 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>「グループを繰り返し実行」関連するコントロールのスクロール ビューで複数のインスタンスを作成しています</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 これにより、ユーザーが同時にいくつかのレコードを表示できます。  
  
## <a name="overview"></a>概要  
 デザイン時に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールは、2 つのセクションで構成されています</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 外部セクションは、*ビューポート*、スクロール可能なデータが実行時に表示されます。 内部の (上部) セクションと呼ばれる、*項目テンプレート*、実行時、データ ソースのフィールドごとに通常&1; つのコントロールに繰り返されるコントロールを配置するには。 プロパティと項目テンプレート内のコントロールにカプセル化されて、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>プロパティ</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>。  
  
 実行時に、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>はバーチャル マシンにコピー<xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>データを表示する、各レコードがビューにスクロールされたときに使用されるオブジェクト</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>。 内の個々 のレコードの表示をカスタマイズすることができます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>イベント、たとえば、それに含まれる値に基づくフィールドを強調表示します</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>。 詳細については、次を参照してください。[方法: DataRepeater コントロールの外観を変更する](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)です。  
  
 最も一般的な用途、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールは、データベース テーブルまたはその他のバインドされたデータ ソースからデータを表示する</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 他に、[!INCLUDE[vstecado](../../../csharp/programming-guide/concepts/linq/includes/vstecado_md.md)]データ オブジェクト、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールを実装するクラスにバインドできます、<xref:System.Collections.IList>インターフェイス (配列を含む) を実装するクラス、<xref:System.ComponentModel.IListSource>インターフェイスを実装するクラス、<xref:System.ComponentModel.IBindingList>インターフェイス、または任意のクラスを実装する、<xref:System.ComponentModel.IBindingListView>インターフェイス</xref:System.ComponentModel.IBindingListView></xref:System.ComponentModel.IBindingList></xref:System.ComponentModel.IListSource></xref:System.Collections.IList></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
### <a name="data-binding"></a>データ バインディング  
 通常からフィールドをドラッグしてデータ バインディングを行う、**データ ソース**ウィンドウ、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 詳細については、次を参照してください。[方法: DataRepeater コントロールにバインドされているデータを表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)します。  
  
 大量のデータを使用する場合は、設定、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>プロパティを`True`に利用可能なデータのサブセットを表示します</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A>。 仮想モードが元のデータ キャッシュの実装では、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>が表示されたら、および実行時にデータ キャッシュのすべての対話を制御する必要があります</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 詳細については、次を参照してください。 [DataRepeater コントロールでの仮想モード](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md)します。  
  
 非バインド コントロールを表示することも、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 たとえば、項目ごとに繰り返されるイメージを表示できます。 詳細については、次を参照してください。[方法: DataRepeater コントロールにバインドされていないコントロールを表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)します。  
  
### <a name="events"></a>イベント  
 最も重要なイベント、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールは、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>ビューに新しい項目がスクロールされたときに発生するイベントと<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>項目が選択されているときに発生するイベントです</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem></xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 使用することができます、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>項目の外観を変更するイベントです</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>。 たとえば、負の値を強調表示することができます。 使用して、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>項目を選択するとコントロールの値にアクセスするイベントです</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.CurrentItemIndexChanged>。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロールは、コード エディターですべて標準のコントロールのイベントを公開します</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 ただし、一部のイベントは使用されません。 キーボードし、マウス イベントをなど`KeyDown`、 `Click`、および`MouseDown`ために、実行時に生成されなくなります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>コントロール自体にフォーカスがあることはありません</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>実行時にのみ作成されるため、デザイン時にイベントを公開しないしません</xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem>。 キーボードとマウスのイベントを処理するかどうかを追加する、<xref:System.Windows.Forms.Panel>コントロールを<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>で<xref:System.Windows.Forms.Panel>.</xref:System.Windows.Forms.Panel>のイベントを処理し、デザイン時と</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A></xref:System.Windows.Forms.Panel> 詳細については、次を参照してください。 [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)します。  
  
### <a name="customizations"></a>カスタマイズ  
 動作と外観をカスタマイズする方法はたくさんあります、<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>実行時およびデザイン時の両方を制御します</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>。 プロパティは、色を変更する、非表示にする、項目ヘッダーを変更または、方向と水平方向への垂直方向から変更を設定できます。 詳細については、次を参照してください。[する方法: DataRepeater コントロールの外観を変更する](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)、[する方法: DataRepeater コントロールに項目ヘッダーを表示](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)、および[する方法: DataRepeater コントロールのレイアウトを変更する](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)です。  
  
 一部のプロパティが<xref:Microsoft.VisualBasic.PowerPacks.DataRepeater><xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>。</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.ItemTemplate%2A>にのみ適用されるものも、コントロール自体</xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>に適用されます。 プロパティを設定する前に、コントロールの適切な部分があることを確認します。 詳細については、次を参照してください。[方法: DataRepeater コントロールの外観を変更する](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)です。  
  
 その他のカスタマイズには、レコードを追加または削除の権限の制御、検索機能の追加、およびマスター/詳細形式で関連データの表示が含まれます。 詳細については、次を参照してください。[する方法: DataRepeater の項目の削除の追加を無効にすると](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)、[方法: DataRepeater コントロールに検索データ](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)、および[する方法: マスター/詳細フォームを使用しての&2; つ DataRepeater コントロール (Visual Studio) を作成する](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)です。  
  
## <a name="see-also"></a>関連項目  
 [DataRepeater コントロール](../../../visual-basic/developing-apps/windows-forms/datarepeater-control-visual-studio.md)   
 [チュートリアル: DataRepeater コントロールにデータを表示します。](../../../visual-basic/developing-apps/windows-forms/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio.md)   
 [DataRepeater コントロールのトラブルシューティング](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
