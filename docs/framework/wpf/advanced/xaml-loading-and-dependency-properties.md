---
title: XAML 読み込みと依存関係プロパティ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom dependency properties [WPF]
- dependency properties [WPF], XAML loading and
- loading XML data [WPF]
ms.assetid: 6eea9f4e-45ce-413b-a266-f08238737bf2
ms.openlocfilehash: 28e121e73ad4bd8ab70aed5f651418eb309b0c03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547727"
---
# <a name="xaml-loading-and-dependency-properties"></a>XAML 読み込みと依存関係プロパティ
現在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の実装、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、本質的に依存関係プロパティに注意してください。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]バイナリを読み込むときに、プロセッサが依存関係プロパティのシステムのプロパティのメソッドを使用[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]と依存関係プロパティの属性を処理します。 これにより、プロパティのラッパーが実質的にはスキップします。 この動作を考慮する必要があり、システムのプロパティ メソッド以外のプロパティのラッパーで、他のコードを配置しないでくださいカスタム依存関係プロパティを実装するときに<xref:System.Windows.DependencyObject.GetValue%2A>と<xref:System.Windows.DependencyObject.SetValue%2A>です。  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、コンシューマーと作成者の両方の依存関係プロパティを理解して、読み取りが[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)と[依存関係プロパティのカスタム](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)です。 必要がありますもを読んだ[XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)と[XAML 構文の詳細](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)です。  
  
<a name="implementation"></a>   
## <a name="the-wpf-xaml-loader-implementation-and-performance"></a>XAML の WPF ローダーの実装とパフォーマンス  
 負荷の大きい計算コストが低い依存関係プロパティとしてプロパティを識別し、プロパティ システムへのアクセスは実装上の理由から、<xref:System.Windows.DependencyObject.SetValue%2A>なく、プロパティのラッパーと、set アクセス操作子を使用して設定します。 これは、ため、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、オブジェクト モデル全体の型およびメンバーのマークアップとさまざまな文字列の構造で示されたリレーションシップを知ることのみを基になるコードを推測する必要があります。  
  
 種類は、xmlns とアセンブリの属性が属性として設定されているをサポートすることを決定する、メンバーを識別するの組み合わせによって検索され、広範なリフレクション プロパティの値をサポートするどのような種類がそれ以外の場合は解決する必要があります。使用して<xref:System.Reflection.PropertyInfo>です。 特定の種類の依存関係プロパティがプロパティ システムを通じてストレージ テーブルとしてアクセスできるため、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の実装、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、このテーブルを使用しのプロパティを指定された*ABC*呼び出すことによってより効率的に設定できる<xref:System.Windows.DependencyObject.SetValue%2A>に含まれている<xref:System.Windows.DependencyObject>依存関係プロパティの識別子を使用して、型を派生*ABCProperty*です。  
  
<a name="implications"></a>   
## <a name="implications-for-custom-dependency-properties"></a>カスタム依存関係プロパティの影響  
 現在[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]の実装、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロパティの設定のプロセッサの動作がまったくラッパーをバイパスする、カスタムの依存関係プロパティのラッパーのセットの定義に追加のロジックを配置する必要がありますされません。 セットの定義でこのようなロジックを配置するかどうかは、プロパティ設定されている場合、ロジックは実行されません[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]コードではなくです。  
  
 同様に、その他のさまざまな、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]からプロパティ値を取得するプロセッサ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]処理の使用も<xref:System.Windows.DependencyObject.GetValue%2A>ラッパーを使用してではなくです。 そのため、またしないでで実装、`get`を超えて定義、<xref:System.Windows.DependencyObject.GetValue%2A>呼び出します。  
  
 次の例は、ラッパーでとしてプロパティの識別子を格納する場所と推奨される依存関係プロパティの定義、 `public` `static` `readonly`フィールド、および`get`と`set`定義にコードが含まれていませんバックアップの依存関係プロパティを定義するために必要なプロパティ システム方法です。  
  
 [!code-csharp[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAquariumSln/CSharp/WPFAquariumObjects/Class1.cs#agwithwrapper)]
 [!code-vb[WPFAquariumSln#AGWithWrapper](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAquariumSln/visualbasic/wpfaquariumobjects/class1.vb#agwithwrapper)]  
  
## <a name="see-also"></a>関連項目  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [コレクション型依存関係プロパティ](../../../../docs/framework/wpf/advanced/collection-type-dependency-properties.md)  
 [依存関係プロパティのセキュリティ](../../../../docs/framework/wpf/advanced/dependency-property-security.md)  
 [DependencyObject の安全なコンストラクター パターン](../../../../docs/framework/wpf/advanced/safe-constructor-patterns-for-dependencyobjects.md)
