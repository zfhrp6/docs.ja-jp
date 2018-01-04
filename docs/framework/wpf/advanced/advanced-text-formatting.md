---
title: "テキストの高度な書式設定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- formatting [WPF]
- text [WPF]
- typography [WPF], text formatting
ms.assetid: f0a7986e-f5b2-485c-a27d-f8e922022212
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bb2664b267301fdf1e3a67e385595a5d28212bc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-text-formatting"></a>テキストの高度な書式設定
[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]堅牢な一連の提供[!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)]アプリケーションにテキストを含めるためです。 レイアウトと[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)][!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]など<xref:System.Windows.Controls.TextBlock>一般のテキスト表現の要素の使用を最も一般的な提供します。 描画[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]など<xref:System.Windows.Media.GlyphRunDrawing>と<xref:System.Windows.Media.FormattedText>図面に書式付きテキストを含めるための手段を提供します。 高度なレベルでは、一番[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]形式設定エンジンは、テキスト ストアの管理、実行テキスト書式管理、および埋め込みオブジェクトの管理などのテキストのプレゼンテーションのすべての側面を制御する、拡張可能なテキストを提供します。  
  
 このトピックを紹介[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]テキストの書式設定します。 クライアントの実装との使用に焦点を当てています、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]テキスト形式設定エンジンです。  
  
> [!NOTE]
>  このドキュメント内のすべてのコード例は含まれて、[テキスト書式設定のサンプルの高度な](http://go.microsoft.com/fwlink/?LinkID=159965)します。  
  

  
<a name="prereq"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、上位レベルに慣れていることを前提と[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]のテキスト表現を使用します。 ほとんどのユーザー シナリオでは、高度なテキストの書式設定も必要ありませんが[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]このトピックで説明します。 概要については、さまざまなテキスト[!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]を参照してください[WPF のドキュメントの](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)します。  
  
<a name="section1"></a>   
## <a name="advanced-text-formatting"></a>テキストの高度な書式設定  
 テキスト レイアウトと[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]コントロールで[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]アプリケーションに簡単に書式付きテキストを追加することは書式設定のプロパティを提供します。 これらのコントロールでは、テキストの表示を処理するさまざまなプロパティが公開されます。書体、大きさ、色などです。 通常の状況では、これらのコントロールはアプリケーションの大半のテキスト表示を処理できます。 しかしながら、一部の高度なシナリオでは、テキスト表示と同様にテキスト保存を制御する必要があります。 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] は、その目的のための拡張テキスト書式設定エンジンを提供します。  
  
 高度な書式設定機能が検出された[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]エンジン、テキスト ストア、テキスト ランを書式設定とプロパティを書式設定テキストで構成されます。 テキスト形式設定エンジン、<xref:System.Windows.Media.TextFormatting.TextFormatter>プレゼンテーションをするためのテキストの行を作成します。 これは行の書式設定プロセスを開始して、テキストのフォーマッタを呼び出すことで実現<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>です。 テキスト フォーマッタは、ストアを呼び出すことによって、テキスト ストアからテキスト ランを取得<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>メソッドです。 <xref:System.Windows.Media.TextFormatting.TextRun>オブジェクトを形成し、<xref:System.Windows.Media.TextFormatting.TextLine>テキスト フォーマッタでオブジェクトを検査または表示するため、アプリケーションを指定します。  
  
<a name="section2"></a>   
## <a name="using-the-text-formatter"></a>テキスト フォーマッタを使用する  
 <xref:System.Windows.Media.TextFormatting.TextFormatter>[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]テキストの書式設定エンジンし、書式設定し、テキストの行の重大なサービスを提供します。 テキスト フォーマッタは、さまざまなテキスト文字書式や段落スタイルを処理し、国際的なテキスト レイアウトに対応しています。  
  
 従来のテキストとは異なり[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]、<xref:System.Windows.Media.TextFormatting.TextFormatter>コールバック メソッドのセットを使用して、テキスト レイアウト クライアントと対話します。 実装でこれらのメソッドを提供するために必要な<xref:System.Windows.Media.TextFormatting.TextSource>クラスです。 次の図は、クライアント アプリケーション間のテキスト レイアウトの相互作用と<xref:System.Windows.Media.TextFormatting.TextFormatter>です。  
  
 ![テキスト レイアウト クライアントと TextFormatter のダイアグラム](../../../../docs/framework/wpf/advanced/media/textformatter01.png "TextFormatter01")  
アプリケーションと TextFormatter の間の相互作用  
  
 テキスト フォーマッタを使用して、テキスト ストアから書式付きテキスト行を取得するの実装は<xref:System.Windows.Media.TextFormatting.TextSource>します。 これを使用してテキスト フォーマッタのインスタンスを作成することで、<xref:System.Windows.Media.TextFormatting.TextFormatter.Create%2A>メソッドです。 このメソッドはテキスト フォーマッタのインスタンスを作成し、行の高さと幅の最大値を設定します。 呼び出して行の作成プロセスを開始するテキスト フォーマッタのインスタンスが作成されしだい、<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>メソッドです。 <xref:System.Windows.Media.TextFormatting.TextFormatter>返信テキストとテキストの実行のための書式設定のパラメーターを取得するテキストのソースにそのフォーム行です。  
  
 次の例は、テキスト ストアを書式設定するプロセスを示しています。 <xref:System.Windows.Media.TextFormatting.TextFormatter>テキスト ストアからテキスト行を取得しに描画テキスト行の書式を設定するオブジェクトが使用される、<xref:System.Windows.Media.DrawingContext>です。  
  
 [!code-csharp[TextFormatterExample#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextFormatterExample#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/Window1.xaml.vb#100)]  
  
<a name="section3"></a>   
## <a name="implementing-the-client-text-store"></a>クライアント テキスト ストアを実装する  
 テキスト書式設定エンジンを拡張するとき、テキスト ストアのあらゆる側面を実装し、管理する必要があります。 これは簡単な作業ではありません。 テキスト ストアは、テキスト ランのプロパティ、段落のプロパティ、埋め込みオブジェクト、その他の同様のコンテンツの追跡を担当します。 個人と共にテキスト フォーマッタも用意されています<xref:System.Windows.Media.TextFormatting.TextRun>テキスト フォーマッタを使用して作成されるオブジェクト<xref:System.Windows.Media.TextFormatting.TextLine>オブジェクト。  
  
 文字列ストアの仮想化を処理するには、テキスト ストアをから派生しなければなりません<xref:System.Windows.Media.TextFormatting.TextSource>です。 <xref:System.Windows.Media.TextFormatting.TextSource>テキスト フォーマッタで使用するテキスト ストアからテキスト ランを取得する方法を定義します。 <xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>テキストを取得するテキスト フォーマッタで使用されるメソッドの実行に使用される行の書式設定には、します。 呼び出し<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>次の条件のいずれかが発生するまでにテキスト フォーマッタによって繰り返し行われました。  
  
-   A<xref:System.Windows.Media.TextFormatting.TextEndOfLine>またはサブクラスが返されます。  
  
-   テキスト ランの蓄積された幅を超えるテキスト フォーマッタを作成するか、通話やテキスト フォーマッタへの呼び出しで指定された行の最大幅<xref:System.Windows.Media.TextFormatting.TextFormatter.FormatLine%2A>メソッドです。  
  
-   A [!INCLUDE[TLA#tla_unicode](../../../../includes/tlasharptla-unicode-md.md)] "CF"、"LF"、"CRLF"などの改行文字のシーケンスが返されます。  
  
<a name="section4"></a>   
## <a name="providing-text-runs"></a>テキスト ランを提供する  
 テキスト書式設定プロセスの中心となるものは、テキスト フォーマッタとテキスト ストアの間のやりとりです。 実装<xref:System.Windows.Media.TextFormatting.TextSource>テキスト フォーマッタの提供、<xref:System.Windows.Media.TextFormatting.TextRun>オブジェクトおよびプロパティのテキストを実行すると、書式を設定します。 この連携では、によって処理される、<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>テキスト フォーマッタによって呼び出されるメソッド。  
  
 次の表は、定義済みのいくつか<xref:System.Windows.Media.TextFormatting.TextRun>オブジェクト。  
  
|TextRun の種類|使用法|  
|------------------|-----------|  
|<xref:System.Windows.Media.TextFormatting.TextCharacters>|文字グリフの表示をテキスト フォーマッタに返すために使用される特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEmbeddedObject>|テキスト内のボタンやイメージなど、測定、ヒット テスト、描画が全部行われるコンテンツを提供するための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfLine>|行の終わりをマークするための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>|段落の終わりをマークするための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>|特殊化されたテキスト ランの使用に影響を受けた、前のスコープを終了するなど、セグメントの末尾を示す<xref:System.Windows.Media.TextFormatting.TextModifier>を実行します。|  
|<xref:System.Windows.Media.TextFormatting.TextHidden>|隠れ文字の範囲をマークするための特殊なテキスト ラン。|  
|<xref:System.Windows.Media.TextFormatting.TextModifier>|その範囲でテキスト ランのプロパティを変更するための特殊なテキスト ラン。 次の一致するまでの範囲<xref:System.Windows.Media.TextFormatting.TextEndOfSegment>テキスト ラン、または、次へ<xref:System.Windows.Media.TextFormatting.TextEndOfParagraph>です。|  
  
 定義済みの<xref:System.Windows.Media.TextFormatting.TextRun>オブジェクトをサブクラス化することができます。 それにより、テキスト ソースはテキスト フォーマッタにカスタム データを含むテキスト ランを提供できます。  
  
 次の例で、<xref:System.Windows.Media.TextFormatting.TextSource.GetTextRun%2A>メソッドです。 このテキスト ストア<xref:System.Windows.Media.TextFormatting.TextRun>テキスト フォーマッタにするオブジェクト。  
  
 [!code-csharp[TextFormatterExample#101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFormatterExample/CSharp/CustomTextSource.cs#101)]
 [!code-vb[TextFormatterExample#101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFormatterExample/VisualBasic/CustomTextSource.vb#101)]  
  
> [!NOTE]
>  この例では、テキスト ストアはすべてのテキストに同じテキスト プロパティを提供します。 高度なテキスト ストアでは、場合によっては、独自のスパン管理を実装し、個々の文字に異なるプロパティを与えるようにする必要があります。  
  
<a name="section5"></a>   
## <a name="specifying-formatting-properties"></a>書式設定プロパティを指定する  
 <xref:System.Windows.Media.TextFormatting.TextRun>オブジェクトは、テキスト ストアによって提供されるプロパティを使用して書式設定されます。 これらのプロパティには、次の 2 つの種類で<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>と<xref:System.Windows.Media.TextFormatting.TextRunProperties>です。 <xref:System.Windows.Media.TextFormatting.TextParagraphProperties>段落の包括的なプロパティをなどに処理<xref:System.Windows.TextAlignment>と<xref:System.Windows.FlowDirection>です。 <xref:System.Windows.Media.TextFormatting.TextRunProperties>各テキスト ラン前景ブラシなど、段落内のさまざまなことができるプロパティは、 <xref:System.Windows.Media.Typeface>、およびフォント サイズ。 カスタムの段落およびカスタム テキスト プロパティの型を実装する、アプリケーションがから派生するクラスを作成する必要があります<xref:System.Windows.Media.TextFormatting.TextParagraphProperties>と<xref:System.Windows.Media.TextFormatting.TextRunProperties>それぞれします。  
  
## <a name="see-also"></a>参照  
 [WPF のタイポグラフィ](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)  
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)
