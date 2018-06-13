---
title: '方法 : イメージ メタデータを読み取る'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- metadata [Windows Forms], property item
- metadata [Windows Forms], reading image
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
ms.openlocfilehash: 92ce4eb8d51fbd25f9a129a629dc47bfb9941f34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526579"
---
# <a name="how-to-read-image-metadata"></a>方法 : イメージ メタデータを読み取る
一部のイメージ ファイルには、イメージの機能を決定するために読み取ることができますメタデータが含まれます。 たとえば、デジタル写真には、make とイメージをキャプチャするために使用する、カメラのモデルを決定するために読み取ることができますメタデータが含まれます可能性があります。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]既存のメタデータを読み取ることができます、およびイメージ ファイルに新しいメタデータを記述することもできます。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 内のメタデータの個々 の部分を格納、<xref:System.Drawing.Imaging.PropertyItem>オブジェクト。 読み取ることができます、<xref:System.Drawing.Image.PropertyItems%2A>のプロパティ、<xref:System.Drawing.Image>ファイルからすべてのメタデータを取得するオブジェクト。 <xref:System.Drawing.Image.PropertyItems%2A>プロパティの配列を返します<xref:System.Drawing.Imaging.PropertyItem>オブジェクト。  
  
 A<xref:System.Drawing.Imaging.PropertyItem>オブジェクトには次の 4 つのプロパティ: `Id`、 `Value`、 `Len`、および`Type`です。  
  
## <a name="id"></a>ID  
 メタデータ アイテムを識別するタグです。 いくつかの値を割り当てることのできる<xref:System.Drawing.Imaging.PropertyItem.Id%2A>次の表に表示されます。  
  
|16 進値|説明|  
|-----------------------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|イメージのタイトル<br /><br /> 相手先ブランド供給<br /><br /> 機器のモデル<br /><br /> ExifDTOriginal<br /><br /> Exif 露出時間<br /><br /> 輝度テーブル<br /><br /> 色光度テーブル|  
  
## <a name="value"></a>[値]  
 値の配列。 値の形式はによって決まります、<xref:System.Drawing.Imaging.PropertyItem.Type%2A>プロパティです。  
  
## <a name="len"></a>Len  
 値の配列の長さ (バイト) を指す、<xref:System.Drawing.Imaging.PropertyItem.Value%2A>プロパティです。  
  
## <a name="type"></a>型  
 配列内の値のデータ型を指す、`Value`プロパティです。 によって示される形式、`Type`プロパティの値は次の表に表示されます  
  
|数値の値|説明|  
|-------------------|-----------------|  
|1|`Byte`。|  
|2|配列`Byte`ascii 形式でエンコードされたオブジェクト|  
|3|16 ビット整数|  
|4|32 ビット整数|  
|5|2 つの配列`Byte`有理数を表すオブジェクト|  
|6|未使用|  
|7|未定義|  
|8|未使用|  
|9|`SLong`|  
|10|`SRational`|  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次のコード例を読み取ったり、ファイルのメタデータの 7 つの部分を表示`FakePhoto.jpg`です。 リストの 2 つ目 (インデックス 1) プロパティ項目が<xref:System.Drawing.Imaging.PropertyItem.Id%2A>0x010F (供給) および<xref:System.Drawing.Imaging.PropertyItem.Type%2A>2 (ASCII エンコードのバイト配列)。 コード例では、そのプロパティ項目の値を表示します。  
  
 コードには、次のような出力が生成されます。  
  
 `Property Item 0`  
  
 `id: 0x320`  
  
 `type: 2`  
  
 `length: 16 bytes`  
  
 `Property Item 1`  
  
 `id: 0x10f`  
  
 `type: 2`  
  
 `length: 17 bytes`  
  
 `Property Item 2`  
  
 `id: 0x110`  
  
 `type: 2`  
  
 `length: 7 bytes`  
  
 `Property Item 3`  
  
 `id: 0x9003`  
  
 `type: 2`  
  
 `length: 20 bytes`  
  
 `Property Item 4`  
  
 `id: 0x829a`  
  
 `type: 5`  
  
 `length: 8 bytes`  
  
 `Property Item 5`  
  
 `id: 0x5090`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `Property Item 6`  
  
 `id: 0x5091`  
  
 `type: 3`  
  
 `length: 128 bytes`  
  
 `The equipment make is Northwind Camera.`  
  
### <a name="code"></a>コード  
 [!code-csharp[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` を必要とします。 フォームの処理<xref:System.Windows.Forms.Control.Paint>イベントとペイントのイベント ハンドラーに次のコードを貼り付けます。 置き換える必要があります`FakePhoto.jpg`イメージの名前と、システムとインポートの有効なパスと、`System.Drawing.Imaging`名前空間。  
  
## <a name="see-also"></a>関連項目  
 [イメージ、ビットマップ、メタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
