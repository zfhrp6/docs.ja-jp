---
title: x:Null のマークアップ拡張機能
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
caps.latest.revision: 20
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8f176598db00c57159bf351ea5d9ec428c5c04bc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="xnull-markup-extension"></a>x:Null のマークアップ拡張機能
指定`null`XAML メンバーに対する値として。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>コメント  
 C# の場合は null 参照用のキーワードと[!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)]が null です。 Null 参照の Microsoft Visual Basic キーワードは、 `Nothing`、常に使用するが、 `{x:Null}` XAML の使用方法に関係なく、XAML と関連付けた分離コード言語として。  
  
 `x:Null`マークアップ拡張機能には設定可能なプロパティはありません。  
  
 Null の使用状況は、XAML メンバーの公開を CLR に関連付けられて多くの場合、<xref:System.Nullable%601>値。  
  
 `x:Null`マークアップ拡張機能のすべての XAML マークアップ拡張機能と同様に、中かっこを使用して (`{,}`) 以外のリテラルまたはイベント ハンドラーの参照を属性値の処理をエスケープします。 属性構文では、このマークアップ拡張機能で最も頻繁に使用される構文です。 オブジェクトの要素の構文`<x:Null />`技術的に可能ですが、めったに使用されないため、`x:Null`マークアップ拡張機能には、位置指定パラメーター、または構築引数はありません。  
  
 マークアップ拡張機能の概要については、次を参照してください。[マークアップ拡張機能と WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)です。  
  
 .NET Framework XAML サービスで、このマークアップ拡張機能の処理がによって定義された、<xref:System.Windows.Markup.NullExtension>クラスです。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 なお`null`必ずしも参照型の依存関係プロパティの初期設定されていない値ではありません。 既定の初期値は、依存関係プロパティごとに異なることができ、プロパティ固有のメタデータに基づくことができます。 多くの依存関係プロパティを受け入れない`null`マークアップまたはコードの検証コールバックの実装のための値として。 依存関係プロパティの詳細については、次を参照してください。[依存関係プロパティの概要](../../../docs/framework/wpf/advanced/dependency-properties-overview.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.DependencyProperty.UnsetValue>  
 [XAML の概要 (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [マークアップ拡張機能と WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
