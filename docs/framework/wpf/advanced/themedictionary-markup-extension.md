---
title: ThemeDictionary のマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
ms.openlocfilehash: ea7c630be3f6d208f5c62e8b9e24606ff0df8466
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547408"
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary のマークアップ拡張機能
カスタム コントロールの作成者やサード パーティ製コントロールをコントロールのスタイル設定に使用するテーマ固有のリソース ディクショナリを読み込めませんを統合するアプリケーションの手段を提供します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`assemblyUri`|[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]テーマ情報を格納するアセンブリのです。 通常、これは、パッケージのより大きなパッケージ内のアセンブリを参照する URI です。 アセンブリ リソースとパッケージの Uri は、展開に関する問題を簡略化します。 詳細については、次を参照してください。 [WPF のパック Uri](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)です。|  
  
## <a name="remarks"></a>コメント  
 1 つだけの特定のプロパティ値を入力するためのものは、この拡張機能: 値を<xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>です。  
  
 この拡張機能を使用すると、される場合にのみを使用するいくつかのスタイルを含む単一リソース専用のアセンブリを指定することができます、 [!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)] Luna テーマがアクティブ、ためには、他のスタイル、ユーザーのシステムにテーマを適用します。 この拡張機能を使用すると、コントロールに固有のリソース ディクショナリの内容に自動的に無効にして再読み込みするために必要なときに別のテーマの特定をします。  
  
 `assemblyUri`文字列 (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>プロパティの値) を特定のテーマに適用するディクショナリを識別する名前付け規則の基礎を形成します。 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>のロジック`ThemeDictionary`生成することによって、規則を完了する、[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]プリコンパイル済みのリソース アセンブリ内に含まれるように特定のテーマのディクショナリのバリアント型を指しています。 この規則、または一般的なコントロールのスタイル設定と、概念としてページ/アプリケーション レベルのスタイル設定のテーマの相互作用を記述するについては、完全にここで説明しません。 使用するための基本的なシナリオ`ThemeDictionary`を指定する、<xref:System.Windows.ResourceDictionary.Source%2A>のプロパティ、`ResourceDictionary`アプリケーション レベルで宣言します。 指定すると、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]によるアセンブリの`ThemeDictionary`拡張機能ではなく、直接[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]、拡張機能のロジックはシステムのテーマが変更されるたびに適用される無効化ロジックを提供します。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 `ThemeDictionary` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> 拡張クラスの <xref:System.Windows.ThemeDictionaryExtension> 値として割り当てられます。  
  
 `ThemeDictionary` オブジェクトの要素の構文にも使用できます。 この例では、値を指定する、<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>プロパティは必須です。  
  
 `ThemeDictionary` は、<xref:System.Windows.Markup.StaticExtension.Member%2A> プロパティをプロパティおよび値のペアとして指定する詳細出力属性使用でも使用できます。  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 詳細出力の使用は、複数の設定可能プロパティを持つ拡張機能や、一部のプロパティがオプションである場合に役立ちます。 `ThemeDictionary` には、必須の設定可能プロパティが 1 つしか存在しないため、このような詳細出力の使用は一般的ではありません。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの実装でこのマークアップ拡張機能の処理が定義されている、<xref:System.Windows.ThemeDictionaryExtension>クラスです。  
  
 `ThemeDictionary` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 すべてのマークアップ拡張機能で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、{、}、規則は、それぞれの属性構文内の文字、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサは、マークアップ拡張機能が、属性を処理する必要がありますを認識します。 詳細については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。  
  
## <a name="see-also"></a>関連項目  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [XAML の概要 (WPF)](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [マークアップ拡張機能と WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)
