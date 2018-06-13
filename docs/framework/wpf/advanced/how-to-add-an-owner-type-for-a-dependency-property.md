---
title: '方法 : 依存関係プロパティの所有者の種類を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: bf3f73743d1c76145bf520ed859c27c4d3aaf662
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542777"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>方法 : 依存関係プロパティの所有者の種類を追加する
この例では、異なる種類の登録されている依存関係プロパティの所有者としてクラスを追加する方法を示します。 これには、手順を実行して、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]リーダーとプロパティ システムの両方のプロパティの追加の所有者として、クラスを認識することができます。 必要に応じて、所有者として追加すると、型固有のメタデータを提供する追加のクラスができます。  
  
 次の例では、`StateProperty`はプロパティでは登録、`MyStateControl`クラスです。 クラス`UnrelatedStateControl`の所有者として追加自体、`StateProperty`を使用して、<xref:System.Windows.DependencyProperty.AddOwner%2A>メソッド、具体的には、署名を使用するように、追加の型に存在する依存関係プロパティの新しいメタデータは、します。 通知を提供する[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]に示した例のようなプロパティのアクセサーでは、[依存関係プロパティを実装して](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md)などとして再追加するクラスに依存関係プロパティの識別子を公開所有者。  
  
 ラッパーの依存関係プロパティは機能を使用したプログラムによるアクセスの観点から<xref:System.Windows.DependencyObject.GetValue%2A>または<xref:System.Windows.DependencyObject.SetValue%2A>です。 通常では、このプロパティのシステム動作を並列たいが、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]プロパティのラッパー。 ラッパーをプログラムでは、依存関係プロパティを設定するが容易し、可能としてプロパティを設定する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]属性。  
  
 既定のメタデータをオーバーライドする方法を調べるには、次を参照してください。[依存関係プロパティのメタデータをオーバーライド](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md)です。  
  
## <a name="example"></a>例  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>関連項目  
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
