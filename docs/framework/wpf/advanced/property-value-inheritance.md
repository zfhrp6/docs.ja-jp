---
title: プロパティ値の継承
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [WPF], property values
- value inheritance [WPF]
- properties [WPF], value inheritance
ms.assetid: d7c338f9-f2bf-48ed-832c-7be58ac390e4
ms.openlocfilehash: 6af356d1c6325714fbc98cd5fe8c3ebc1825fcb1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547395"
---
# <a name="property-value-inheritance"></a>プロパティ値の継承
プロパティ値の継承は、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] プロパティ システムの機能です。 プロパティ値の継承により、要素のツリー内の子要素は、親要素から特定のプロパティの値を取得できます。これは、最も近い親要素のいずれかに設定されているとおりにその値を継承することで行われます。 親要素もプロパティ値の継承を通じてその値を取得している場合があるため、システムはページ ルートまで再帰している可能性があります。 プロパティ値の継承は、プロパティ システムの既定の動作ではありません。あるプロパティに子要素でのプロパティ値の継承を実行させるには、そのプロパティに特定のメタデータを設定する必要があります。  
  

  
<a name="Property_Value_Inheritance_is_Containment_Inheritance"></a>   
## <a name="property-value-inheritance-is-containment-inheritance"></a>プロパティ値の継承は包含継承である  
 ここで言う "継承" は、型や一般的なオブジェクト指向プログラミングのコンテキストにおける継承 (派生クラスがその基底クラスからメンバー定義を継承する) とは若干異なる概念です。 この意味での継承は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でも使用されます。さまざまな基底クラスで定義されたプロパティは、要素として使用される場合の派生 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] クラスの属性として、およびコードのメンバーとして公開されます。 プロパティ値の継承は、要素のツリー内の親子のリレーションシップに基づいて、ある要素から別の要素にプロパティ値が継承されるしくみに特に関連します。 その要素のツリーが最も直接的に認識されるのは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] マークアップでアプリケーションを定義する際にさまざまな要素を別の要素内に入れ子にする場合です。 オブジェクトのツリーはプログラムで作成することもできます。これを行うには、オブジェクトを別のオブジェクトの指定したコレクションに追加します。完成したツリーでも、実行時にプロパティ値の継承が同様に動作します。  
  
<a name="Practical_Applications_of_Property_Value_Inheritance"></a>   
## <a name="practical-applications-of-property-value-inheritance"></a>プロパティ値の継承を実際の応用例  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] には、プロパティの継承が有効なプロパティがいくつか含まれています。 これらのプロパティの一般的なシナリオは次のとおりです。これらのプロパティは、ページごとに一度だけ設定するのが適していますが、いずれかの基本要素クラスのメンバーでもあるため、ほとんどの子要素にも存在することになります。 たとえば、<xref:System.Windows.FrameworkElement.FlowDirection%2A>どちらの方向にコンテンツが流し込まれますプロパティ コントロールの表示し、ページ上に配置する必要があります。 通常、テキスト フローの概念は、すべての子要素で一貫して処理される必要があります。 要素ツリーのあるレベルにおいて、何らかの理由でユーザーまたは環境の操作によってフロー方向がリセットされた場合は、一般に要素全体でリセットする必要があります。 ときに、<xref:System.Windows.FrameworkElement.FlowDirection%2A>プロパティが継承に対する、値を設定または 1 回再設定すると、アプリケーション内の各ページのプレゼンテーションのニーズを含む、要素ツリーのレベルでのみ必要があります。 初期既定値であっても、同様の方法で値を継承します。 プロパティ値の継承モデルでは、要素の値を個別にリセットすることもできます。これは、複数のフロー方向の混在を意図したまれなケースに対応するためです。  
  
<a name="Making_a_Custom_Property_Inheritable"></a>   
## <a name="making-a-custom-property-inheritable"></a>カスタム プロパティを継承可能にする  
 カスタム プロパティのメタデータを変更することで、独自のカスタム プロパティを継承可能にすることもできます。 ただし、プロパティを継承可能にする場合は、パフォーマンスについて考慮する必要があります。 ローカル値や、スタイル、テンプレート、またはデータ バインディングから取得した値がそのプロパティに設定されていない場合、継承可能なプロパティは、それ自身に割り当てられた値を論理ツリー内のすべての子要素に提供します。  
  
 プロパティを値の継承に参加させるには、「[添付プロパティを登録する](../../../../docs/framework/wpf/advanced/how-to-register-an-attached-property.md)」の説明に従ってカスタム添付プロパティを作成します。 メタデータを持つプロパティを登録 (<xref:System.Windows.FrameworkPropertyMetadata>) し、そのメタデータ内のオプションの設定で"Inherits"オプションを指定します。 また、値が継承されるようになったため、プロパティに既定値が設定されていることも確認します。 プロパティを添付プロパティとして登録しましたが、"非添付" の依存関係プロパティの場合と同様に、所有者型で get アクセスおよび set アクセスのプロパティ "ラッパー" を作成することもできます。 その後、継承可能なプロパティで設定することも、所有者型または派生型は、ダイレクトのプロパティのラッパーを使用して、またはいずれかで添付プロパティの構文を使用して設定できます<xref:System.Windows.DependencyObject>です。  
  
 添付プロパティは概念的にはプロパティと同様にグローバルです。いずれかの値をチェックすることができます<xref:System.Windows.DependencyObject>および有効な結果を取得します。 添付プロパティの一般的なシナリオは子要素、プロパティの値を設定して、そのシナリオは、該当するプロパティが添付プロパティは常に各要素に対して添付プロパティとして暗黙的に存在する場合より効果的な (<xref:System.Windows.DependencyObject>) ツリーでします。  
  
> [!NOTE]
>  プロパティ値の継承は、非添付依存関係プロパティについても機能しているように見えることがありますが、ランタイム ツリーでの特定の要素の境界を介する非添付プロパティの継承動作は定義されていません。 常に使用する<xref:System.Windows.DependencyProperty.RegisterAttached%2A>を指定するプロパティを登録する<xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>メタデータにします。  
  
<a name="InheritanceContext"></a>   
## <a name="inheriting-property-values-across-tree-boundaries"></a>ツリー境界を越えてプロパティ値を継承する  
 プロパティの継承は、要素のツリーを走査して行われます。 多くの場合、このツリーは論理ツリーに対応します。 ただし、要素のツリーをなどを定義するマークアップに WPF コア レベルのオブジェクトを含めるとするたびに、 <xref:System.Windows.Media.Brush>、不連続の論理ツリーを作成しました。 True の論理ツリーが概念的には及ばないを通じて、<xref:System.Windows.Media.Brush>論理ツリーが WPF フレームワーク レベルの概念であるためです。 ご覧のメソッドを使用する場合、結果に反映<xref:System.Windows.LogicalTreeHelper>です。 ただし、プロパティ値の継承は、論理ツリー内には、このギャップを埋めることができ、継承可能なプロパティが添付プロパティおよびありません意図的な継承のブロックの境界として登録されている限り、引き続きを使用すると、継承された値を渡すことができます (など、 <xref:System.Windows.Controls.Frame>) が発生しました。  
  
## <a name="see-also"></a>関連項目  
 [依存関係プロパティのメタデータ](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md)  
 [添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)  
 [依存関係プロパティ値の優先順位](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)
