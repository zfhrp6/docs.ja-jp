---
title: "PresentationOptions:Freeze 属性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d8f1a876f65941afb159d4c3d8904ab4426d9177
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze 属性
セット、<xref:System.Windows.Freezable.IsFrozen%2A>状態`true`に含まれている<xref:System.Windows.Freezable>要素。 既定の動作、<xref:System.Windows.Freezable>せず、`PresentationOptions:Freeze`属性が指定される<xref:System.Windows.Freezable.IsFrozen%2A>は`false`負荷時、および [全般] に依存<xref:System.Windows.Freezable>実行時に動作します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`PresentationOptions`|名前空間プレフィックス、XML 1.0 仕様あたり、任意の有効なプレフィックス文字列になります。 プレフィックス`PresentationOptions`はこのドキュメントで識別する目的で使用します。|  
|`freezableElement`|いずれかをインスタンス化する要素の派生クラス<xref:System.Windows.Freezable>です。|  
  
## <a name="remarks"></a>コメント  
 `Freeze`属性は、唯一の属性またはで他のプログラミング要素が定義されている、 `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML 名前空間。 `Freeze`に指定できるは、無視できるを使用できるように具体的には、この特別な名前空間の属性が存在する[mc: Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)ルート要素の宣言の一部として。 理由を`Freeze`無視することである必要がありますではないすべて[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの実装は、固定するのには、 <xref:System.Windows.Freezable> ; の読み込み時にこの機能はの一部、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]仕様です。  
  
 処理する機能、`Freeze`属性は、具体的に組み込まれている、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を処理するプロセッサ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のアプリケーションをコンパイルします。 属性は、クラスによってサポートされていませんし、属性構文が拡張または変更します。 実装する場合、独自[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの固定の動作をすることができます、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの処理時に、`Freeze`属性に<xref:System.Windows.Freezable>読み込み時に要素。  
  
 すべての値、`Freeze`以外の属性`true`(いない大文字小文字を区別)、読み込み時にエラーが生成されます。 (を指定する、`Freeze`属性に`false`、エラーではありません設定するため、既定ではない`false`何も行われません)。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Freezable>  
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [mc:Ignorable 属性](../../../../docs/framework/wpf/advanced/mc-ignorable-attribute.md)
