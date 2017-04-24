---
title: "XamlWriter.Save のシリアル化の制限 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "制限 (XamlWriter.Save の)"
  - "シリアル化の制限 (XamlWriter.Save の)"
  - "XamlWriter.Save, シリアル化の制限"
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# XamlWriter.Save のシリアル化の制限
[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] <xref:System.Windows.Markup.XamlWriter.Save%2A> を使用して、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アプリケーションの内容を [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイルとしてシリアル化できます。  ただし、シリアル化される対象には注意すべき制限がいくつかあります。  このトピックでは、これらの制限と全般的な考慮事項をいくつか説明します。  
  
   
  
<a name="Run_Time__Not_Design_Time_Representation"></a>   
## ランタイム \(非デザイン タイム\) 表現  
 <xref:System.Windows.Markup.XamlWriter.Save%2A> の呼び出しによるシリアル化の基本概念は、実行時にシリアル化されているオブジェクトが結果として表れることです。  元の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルのデザイン タイム プロパティの多くは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]がメモリ内オブジェクトとして読み込まれる時点で既に最適化されているか、失われている可能性があり、シリアル化するために<xref:System.Windows.Markup.XamlWriter.Save%2A>を呼び出したときには保持されていません。  シリアル化された結果は、アプリケーションの構築された論理ツリーを効率的に表していますが、必ずしも、これを生成した元の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] のものではありません。  これらの問題により、広範な [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] デザイン サーフェイスの一部として <xref:System.Windows.Markup.XamlWriter.Save%2A> のシリアル化を使用することが極めて困難になります。  
  
<a name="Serialization_is_Self_Contained"></a>   
## シリアル化の内部格納  
 <xref:System.Windows.Markup.XamlWriter.Save%2A> のシリアル化された出力は内部格納されます。つまり、シリアル化されたものはすべて、単一ルート要素と共に [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の単一ページ内に含まれ、[!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)] 以外による外部参照はされません。  たとえば、ページがアプリケーション リソースからリソースを参照した場合、これらのリソースは、シリアル化されているページのコンポーネントであるかのように表示されます。  
  
<a name="Extension_References_are_Dereferenced"></a>   
## 拡張参照の参照解除  
 さまざまなマークアップ エクステンション形式によって作成されたオブジェクトの一般的な参照 \(`StaticResource`、`Binding` など\) は、シリアル化プロセスによって参照解除されます。  これらは、メモリ内のオブジェクトがアプリケーション ランタイムによって作成された時点で既に参照解除されており、<xref:System.Windows.Markup.XamlWriter.Save%2A> ロジックは、このようなシリアル化された出力の参照を復元するために、元の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を再確認することはありません。  これにより、データ バインディングされた値または取得されたリソース値はすべて、ランタイム表現により前回使用された値に潜在的に固定され、ローカルに設定された他の値とこのような値を区別するための限定的または間接的な機能だけを持ちます。  また、プロジェクト内にイメージが存在するので、イメージも、元のソース参照としてではなくイメージへのオブジェクト参照としてシリアル化され、元々参照されていたいかなるファイル名または [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] も失われます。  同一ページ内で宣言されたリソースも、これらが参照されたポイントにシリアル化され、リソース コレクションのキーとしては保持されません。  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## 保持されないイベント処理  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を介して追加されたイベント ハンドラーがシリアル化されない場合、これらは保持されません。  分離コード \(および関連 x:Code 機能\) を持たない [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] は、ランタイム手続きロジックをシリアル化する方法がありません。  シリアル化は内蔵されていて、論理ツリーに制限されているため、イベント ハンドラーを格納するための機能がありません。  その結果、イベント ハンドラー属性 \(属性自体とハンドラーの名前を表す文字列共\) は、出力 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] から削除されます。  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## XAMLWriter.Save を使用するための現実的なシナリオ  
 ここに示された制限は相当な量ですが、<xref:System.Windows.Markup.XamlWriter.Save%2A> をシリアル化に使用するための適切なシナリオがいくつかあります。  
  
-   ベクターまたはグラフィカル出力 : レンダリングされた領域の出力を使用して、再読み込みの際に同じベクターまたはグラフィックスを再現できます。  
  
-   リッチ テキストとフロー ドキュメント : テキストと要素の書式およびその中に含まれる要素のコンテインメントはすべて、出力に保持されます。  これは、クリップボードに近似した機能に役立つ場合があります。  
  
-   ビジネス オブジェクト データの保持 : ビジネス オブジェクトが基本的な [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] 規則 \(カスタム コンストラクターと変換に対し参照ごとのプロパティ値を提供する、など\) に従う限り、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] データなどのデータをカスタム要素に格納した場合、これらのビジネス オブジェクトはシリアル化によって永続的なものになります。