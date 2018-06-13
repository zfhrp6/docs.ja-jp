---
title: XamlWriter.Save のシリアル化の制限
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: cbe8d517b8794f6aae7190457a077422d235acb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547964"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>XamlWriter.Save のシリアル化の制限
[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] <xref:System.Windows.Markup.XamlWriter.Save%2A>の内容をシリアル化に使用できる、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]アプリケーションとして、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ファイル。 ただし、シリアル化されるいくつかの重要な制限があります。 このトピックでは、これらの制限事項といくつかの一般的な考慮事項が記載されています。  
  
 
  
<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>実行時、デザイン時ではない表現  
 呼び出しによって内容がシリアル化の基本的な考え方<xref:System.Windows.Markup.XamlWriter.Save%2A>結果が実行時に、シリアル化されるオブジェクトの表現になることができます。 元の多くのデザイン時プロパティ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルが既に最適化かまたは時間によって失われる可能性を[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]がメモリ内のオブジェクトとして読み込まれると、呼び出すときに保持されない<xref:System.Windows.Markup.XamlWriter.Save%2A>をシリアル化します。 シリアル化された結果は、アプリケーションは必ずしも元は、構築済みの論理ツリーの有効な表現で、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]生成します。 これらの問題非常に難しくを使用する、<xref:System.Windows.Markup.XamlWriter.Save%2A>拡張の一部としてシリアル化[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]デザイン サーフェイスです。  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>シリアル化は、自己完結型  
 シリアル化された出力<xref:System.Windows.Markup.XamlWriter.Save%2A>は自己完結; は、シリアル化するすべてのアイテムに含まれている、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]単一ページで、単一のルート要素と以外の外部参照はありません[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]です。 インスタンスの場合、ページには、アプリケーション リソースからのリソースが参照されている、これらは表示したシリアル化されるページのコンポーネント。  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>拡張機能の参照が逆参照します。  
 一般的なオブジェクトへの参照などのマークアップ拡張機能のさまざまな形式で行われた`StaticResource`または`Binding`、シリアル化プロセスによって逆参照されます。 既にメモリ内オブジェクトには、アプリケーション ランタイムによって作成された時に逆参照されたこれらと<xref:System.Windows.Markup.XamlWriter.Save%2A>ロジックが、元の再表示されません[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]をシリアル化された出力には、このような参照を復元します。 これは、任意のデータ バインドまたは最後に、実行時で表現したローカル設定その他の値からこのような値を区別するためにのみに制限されているか間接の機能を使用する値を指定する値を取得したリソースに可能性のあるフリーズします。 どのようなファイル名が失われる、元のソースの参照ではなく、プロジェクト内に存在するために、イメージはイメージへの参照をオブジェクトとしてシリアル化もまたは[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]元々 参照されています。 同じページ内で宣言されているリソースは、これらが参照されたリソース コレクションのキーとして保持されているのではなく、ポイントにシリアル化された認識されています。  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>イベント処理が保持されません。  
 ときにイベント ハンドラーによって追加された[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]はシリアル化すると、それらは保持されません。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 分離コードなし (および関連する X:code メカニズムがなければ) ランタイム手続き型のロジックをシリアル化の方法がありません。 シリアル化は自己完結型の論理ツリーに限定的であるために、イベント ハンドラーを格納するための機能はありません。 出力からのイベント ハンドラー属性、属性自体と、ハンドラーの名前を示す文字列値の両方を削除するため、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>XAMLWriter.Save の使用についての現実的なシナリオ  
 ここでは、非常に大きくを使用するためのいくつかの適切なシナリオは引き続き、制限事項が表示されているときに<xref:System.Windows.Markup.XamlWriter.Save%2A>シリアル化します。  
  
-   Vector またはグラフィカルな出力: 表示された領域の出力を使用して同じベクターまたは再読み込み時のグラフィックスを再現できます。  
  
-   リッチ テキストとフロー ドキュメント: テキストとすべての要素と要素の書式設定コンテインメント内に、出力に保持されます。 これは、クリップボードに近似した機能に役立ちます。  
  
-   ビジネス オブジェクト データの保持: かどうかに格納しているデータ、カスタム要素など[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データをビジネス オブジェクトは基本的に従う限り[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]カスタム コンス トラクターと変換は参照渡しでプロパティの値を提供するなどのルールこれらのビジネス オブジェクトをする永続的なものシリアル化を使用します。
