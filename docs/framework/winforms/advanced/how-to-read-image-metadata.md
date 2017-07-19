---
title: "方法 : イメージ メタデータを読み取る | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "メタデータ, プロパティ項目"
  - "メタデータ, 読み取り (イメージの)"
ms.assetid: 72ec0b31-0be7-444a-9575-1dbcb864e0be
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : イメージ メタデータを読み取る
一部のイメージ ファイルにはメタデータが含まれており、このデータを読み取って、そのイメージの特徴を確認できます。  デジタル写真にはこのようなメタデータが含まれていることがあり、そのメタデータを読み取って、たとえばイメージを取り込むために使用したカメラのメーカーやモデルを確認できます。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] では、既存のメタデータを読み取ることができるほか、新しいメタデータをイメージ ファイルに書き込むこともできます。  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、個々のメタデータを <xref:System.Drawing.Imaging.PropertyItem> オブジェクトに格納します。  <xref:System.Drawing.Image> オブジェクトの <xref:System.Drawing.Image.PropertyItems%2A> プロパティを読み取ることによって、ファイルからすべてのメタデータを取得できます。  <xref:System.Drawing.Image.PropertyItems%2A> プロパティは、<xref:System.Drawing.Imaging.PropertyItem> オブジェクトの配列を返します。  
  
 <xref:System.Drawing.Imaging.PropertyItem> オブジェクトには、`Id`、`Value`、`Len`、および `Type` という 4 つのプロパティがあります。  
  
## Id  
 メタデータ項目を識別するタグ。  <xref:System.Drawing.Imaging.PropertyItem.Id%2A> に割り当てることのできる値の一部を次の表に示します。  
  
|16 進値|Description|  
|-----------|-----------------|  
|0x0320<br /><br /> 0x010F<br /><br /> 0x0110<br /><br /> 0x9003<br /><br /> 0x829A<br /><br /> 0x5090<br /><br /> 0x5091|イメージのタイトル<br /><br /> 機器のメーカー<br /><br /> 機器のモデル<br /><br /> ExifDTOriginal<br /><br /> Exif 露光時間<br /><br /> 輝度テーブル<br /><br /> クロミナンス テーブル|  
  
## 値  
 値の配列。  値の形式は、<xref:System.Drawing.Imaging.PropertyItem.Type%2A> プロパティによって決定されます。  
  
## Len  
 <xref:System.Drawing.Imaging.PropertyItem.Value%2A> プロパティが指す値配列の長さ \(バイト単位\)。  
  
## 種類  
 `Value` プロパティが指す配列内の値のデータ型。  `Type` プロパティの値で示される形式を次の表に示します。  
  
|数値|Description|  
|--------|-----------------|  
|1|`Byte`|  
|2|ASCII 形式でエンコードされた `Byte` オブジェクトの配列|  
|3|16 ビット整数|  
|4|32 ビット整数|  
|5|有理数を表す 2 つの `Byte` オブジェクトの配列|  
|6|未使用|  
|7|未定義|  
|8|未使用|  
|9|`SLong`|  
|10|`SRational`|  
  
## 例  
  
### Description  
 ファイル `FakePhoto.jpg` からメタデータの 7 つの部分を読み取って表示するコード例を次に示します。  リスト内の 2 番目の \(インデックス 1\) プロパティ項目には、<xref:System.Drawing.Imaging.PropertyItem.Id%2A> 0x010F \(機器のメーカー\) と <xref:System.Drawing.Imaging.PropertyItem.Type%2A> 2 \(ASCII 形式でエンコードされたバイト配列\) が指定されています。  このコード例は、このプロパティ項目の値を表示します。  
  
 このコードは、次のような出力を生成します。  
  
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
  
### コード  
 [!code-csharp[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.WorkingWithImages#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#51)]  
  
## コードのコンパイル  
 前述の例は Windows フォームと一緒に使用することが想定されていて、<xref:System.Windows.Forms.Control.Paint> イベント ハンドラーのパラメーターである <xref:System.Windows.Forms.PaintEventArgs> `e` が必要です。  フォームの <xref:System.Windows.Forms.Control.Paint> イベントを処理し、このコードを Paint のイベント ハンドラーに貼り付けます。  `FakePhoto.jpg` をイメージ名とシステム上の有効なパスに置き換え、`System.Drawing.Imaging` 名前空間をインポートする必要があります。  
  
## 参照  
 [イメージ、ビットマップ、およびメタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)   
 [イメージ、ビットマップ、アイコン、およびメタファイルの操作](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)