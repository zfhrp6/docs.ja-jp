---
title: グラフィックス サービスの 3 つのカテゴリ
ms.date: 03/30/2017
helpviewer_keywords:
- imaging
- graphics [Windows Forms], categories
- 2-D vector graphics
- vector graphics
- typography
ms.assetid: 068c0ef3-f6ee-4d58-a7b6-eb2531ead408
ms.openlocfilehash: 5621a2c0bba2e922e62006feba9ca0381181c780
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525048"
---
# <a name="three-categories-of-graphics-services"></a>グラフィックス サービスの 3 つのカテゴリ
Windows フォームにおけるグラフィックスの提供は、次の 3 つの広範なカテゴリに分類されます。  
  
-   2 次元 (2-d) ベクター グラフィックス  
  
-   イメージング  
  
-   タイポグラフィ  
  
## <a name="2-d-vector-graphics"></a>2 次元ベクター グラフィックス  
 2 次元ベクター グラフィックスはプリミティブです。直線、曲線、および数字; など座標システム上のポイントのセットによって指定されています。 たとえば、直線がその 2 つのエンドポイントで指定されたされ、四角形は、左上隅および幅と高さを定義する数値の 1 組の位置を示す点によって指定されます。 単純なパスは、直線で接続されている点の配列によって指定されます。 ベジエ スプラインは、次の 4 つのコントロール ポイントで指定された高度な曲線です。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] クラスと構造体プリミティブ自体に関する情報を格納する、プリミティブを描画する方法についての情報を格納するクラスと描画を実際に実行するクラスを提供します。 たとえば、<xref:System.Drawing.Rectangle>構造体に格納します四角形のサイズと場所、<xref:System.Drawing.Pen>クラス 線の色、線の幅、および線のスタイルに関する情報を格納および<xref:System.Drawing.Graphics>クラスには、線、四角形、パスを描画するためのメソッドと。他の図。 あるいくつかも<xref:System.Drawing.Brush>方法に関する情報を格納するクラスは閉じた図形とパスが色やパターンで塗りつぶされます。  
  
 メタファイルにグラフィックス コマンドのシーケンスには、ベクター イメージを記録することができます。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供、<xref:System.Drawing.Imaging.Metafile>記録、表示、およびメタファイルを保存するためのクラスです。 <xref:System.Drawing.Imaging.MetafileHeader>と<xref:System.Drawing.Imaging.MetaHeader>クラス、メタファイルのヘッダーに格納されたデータを検査することができます。  
  
## <a name="imaging"></a>イメージング  
 特定の種類の画像は難しいとベクター グラフィックスの手法とを表示します。 たとえば、ツール バー ボタンの画像やアイコンとして表示される画像は、直線と曲線のコレクションとして指定するが困難なです。 いっぱいになった野球場の高解像度デジタル写真はベクター手法を作成するさらに困難です。 この種類のイメージはビットマップで、画面上の個々 のドットの色を表す数値の配列として格納されます。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 提供、<xref:System.Drawing.Bitmap>を表示する、操作、およびビットマップの保存のクラスです。  
  
## <a name="typography"></a>タイポグラフィ  
 文字体裁は、さまざまなフォント、サイズ、およびスタイル内のテキストの表示です。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 複雑なこのタスクに対する広範なサポートを提供します。 新機能のいずれかの[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]サブピクセル アンチ エイリアスによりテキストをレンダリング LCD 画面で滑らかに表示します。  
  
 また、Windows フォームでテキストを描画するためのオプションは[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]機能でその<xref:System.Windows.Forms.TextRenderer>クラスです。  
  
## <a name="see-also"></a>関連項目  
 [グラフィックスの概要](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)  
 [GDI+ マネージ コードについて](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
 [マネージ グラフィックス クラスの使用](../../../../docs/framework/winforms/advanced/using-managed-graphics-classes.md)
