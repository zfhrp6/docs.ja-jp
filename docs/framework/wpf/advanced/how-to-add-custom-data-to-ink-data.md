---
title: '方法 : インク データにカスタム データを追加する'
ms.date: 03/30/2017
helpviewer_keywords:
- ink data [WPF], adding custom data
- InkCanvas [WPF], displaying
ms.assetid: f02aac6f-3436-4f7c-b6ea-0452cba5332c
ms.openlocfilehash: 40d883f3d3e1d504c8757c31325aa72a03da37e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544512"
---
# <a name="how-to-add-custom-data-to-ink-data"></a>方法 : インク データにカスタム データを追加する
カスタム データは、インクがシリアル化するインク形式 (ISF) として保存されるときに保存されるインクを追加することができます。  カスタム データを保存することができます、 <xref:System.Windows.Ink.DrawingAttributes>、 <xref:System.Windows.Ink.StrokeCollection>、または<xref:System.Windows.Ink.Stroke>です。  3 つのオブジェクトのカスタム データを保存できることと、データを保存する最適な場所を決定する機能を提供します。  3 つすべてのクラスでは、同様のメソッドを使用して格納し、カスタム データにアクセスします。  
  
 カスタム データとしては、次の種類のみを保存することができます。  
  
-   <xref:System.Boolean>  
  
-   <xref:System.Boolean>[]  
  
-   <xref:System.Byte>  
  
-   <xref:System.Byte>[]  
  
-   <xref:System.Char>  
  
-   <xref:System.Char>[]  
  
-   <xref:System.DateTime>  
  
-   <xref:System.DateTime>[]  
  
-   <xref:System.Decimal>  
  
-   <xref:System.Decimal>[]  
  
-   <xref:System.Double>  
  
-   <xref:System.Double>[]  
  
-   <xref:System.Int16>  
  
-   <xref:System.Int16>[]  
  
-   <xref:System.Int32>  
  
-   <xref:System.Int32>[]  
  
-   <xref:System.Int64>  
  
-   <xref:System.Int64>[]  
  
-   <xref:System.Single>  
  
-   <xref:System.Single>[]  
  
-   <xref:System.String>  
  
-   <xref:System.UInt16>  
  
-   <xref:System.UInt16>[]  
  
-   <xref:System.UInt32>  
  
-   <xref:System.UInt32>[]  
  
-   <xref:System.UInt64>  
  
-   <xref:System.UInt64>[]  
  
## <a name="example"></a>例  
 次の例では、追加のカスタム データを取得する方法、<xref:System.Windows.Ink.StrokeCollection>です。  
  
 [!code-csharp[HowToAddCustomDataToInk#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#1)]  
  
 次の例を表示するアプリケーションの作成、<xref:System.Windows.Controls.InkCanvas>と 2 つのボタンです。  ボタン、 `switchAuthor`、2 つの異なる作成者によって使用される 2 つのペンを有効にします。  ボタン`changePenColors`上線の色を変更、<xref:System.Windows.Controls.InkCanvas>作成者に従ってします。  2 つのアプリケーション定義<xref:System.Windows.Ink.DrawingAttributes>オブジェクトし、を描いていましたが、著者を示す 1 つずつにカスタム プロパティを追加、<xref:System.Windows.Ink.Stroke>です。  ユーザーがクリックしたとき`changePenColors`アプリケーションがカスタム プロパティの値に従って stroke の外観を変更します。  
  
 [!code-xaml[HowToAddCustomDataToInk#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml#2)]  
  
 [!code-csharp[HowToAddCustomDataToInk#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HowToAddCustomDataToInk/CSharp/Window1.xaml.cs#3)]
