---
title: WPF XAML 名前スコープ
ms.date: 03/30/2017
helpviewer_keywords:
- namescopes [WPF]
- styles [WPF], namescopes in
- templates [WPF], namescopes in
- APIs [WPF], name-related
- name-related APIs
- XAML [WPF], namescopes
- classes [WPF], FrameworkContentElement
ms.assetid: 52bbf4f2-15fc-40d4-837b-bb4c21ead7d4
ms.openlocfilehash: c13dba48d21235c57be64d90b6547902e0428a6e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548695"
---
# <a name="wpf-xaml-namescopes"></a>WPF XAML 名前スコープ
XAML 名前スコープを識別する概念のオブジェクトを XAML で定義されています。 XAML 名前スコープ内の名前は、オブジェクト ツリー内のオブジェクトの XAML で定義された名前と、対応するインスタンス間のリレーションシップを確立するために使用できます。 XAML 名前スコープ通常、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML アプリケーションのルート個々 の XAML ページを読み込むときに、マネージ コードは作成されます。 プログラミング オブジェクトとしての XAML 名前スコープが定義されている、<xref:System.Windows.Markup.INameScope>インターフェイスし、実際のクラスによって実装されても<xref:System.Windows.NameScope>します。  
  
  
  
<a name="Namescopes_in_Loaded_XAML_Applications"></a>   
## <a name="namescopes-in-loaded-xaml-applications"></a>読み込まれた XAML アプリケーションにおける名前スコープ  
 広範なプログラミングまたはコンピューター サイエンスのコンテキストでは、プログラミングの概念が含まれる場合、一意の識別子またはオブジェクトにアクセスするために使用する名前の原則。 内の境界を定義する名前スコープ識別子や名前を使用するシステムでは、その名前のオブジェクトが要求されている場合、プロセスや方法は検索するまたは識別名の一意性が強制されますの境界。 次の一般原則は、XAML 名前スコープの場合は true です。 XAML 名前スコープは、WPF では、ページが読み込まれるときに、XAML ページのルート要素に作成されます。 ページのルートから始まる XAML ページ内で指定した名前は、適切な XAML 名前スコープに追加されます。  
  
 WPF xaml で共通のルート要素である要素 (など<xref:System.Windows.Controls.Page>、および<xref:System.Windows.Window>) 常に XAML 名前スコープを制御します。 場合など、要素<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>マークアップでは、ページのルート要素には、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサを追加、<xref:System.Windows.Controls.Page>暗黙的にルートように、<xref:System.Windows.Controls.Page>作業用の XAML 名前スコープを指定できます。  
  
> [!NOTE]
>  WPF ビルド アクションがない場合でも、XAML 稼働環境の XAML 名前スコープを作成`Name`または`x:Name`内にある要素の属性が定義されている、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ。  
  
 XAML 名前スコープで 2 回、同じ名前を使用しようとすると、例外が発生します。 分離コードがあり、コンパイルされたアプリケーションの一部を WPF xaml で例外はビルド時に、WPF ビルド アクションによって、初期のマークアップのコンパイル時に、ページに対して生成されたクラスを作成するときに発生します。 されていない XAML をマークアップ コンパイルされたすべてのビルド アクションによって、XAML が読み込まれるときに XAML 名前スコープの問題に関連する例外を発生する可能性があります。 XAML デザイナーでは、デザイン時に XAML 名前スコープの問題も予測可能性があります。  
  
### <a name="adding-objects-to-runtime-object-trees"></a>オブジェクトをランタイム オブジェクト ツリーに追加します。  
 XAML が解析した時点では、WPF XAML 名前スコープが作成され、定義の時点を表します。 オブジェクトをオブジェクト ツリーの時点にそのツリーが生成される XAML が解析された後で追加した場合、`Name`または`x:Name`新しいオブジェクトの値が XAML 名前スコープ内の情報を自動的に更新されません。 XAML が読み込まれた後に、WPF XAML 名前スコープにオブジェクトの名前を追加するには、適切な実装を呼び出す必要があります<xref:System.Windows.Markup.INameScope.RegisterName%2A>XAML 名前スコープを定義するオブジェクトのルートである通常 XAML ページ。 名前が登録されていない場合、追加するオブジェクトで参照できません名前メソッドによってなど<xref:System.Windows.FrameworkElement.FindName%2A>、およびアニメーションのターゲットの名前を使用することはできません。  
  
 アプリケーション開発者向けの最も一般的なシナリオは、使用する<xref:System.Windows.FrameworkElement.RegisterName%2A>ページの現在のルートに XAML 名前スコープに名前を登録します。 <xref:System.Windows.FrameworkElement.RegisterName%2A> ストーリー ボードの重要なシナリオの一部のアニメーションでそのターゲット オブジェクトです。 詳細については、次を参照してください。[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)です。  
  
 呼び出す場合<xref:System.Windows.FrameworkElement.RegisterName%2A>XAML 名前スコープを定義するオブジェクト以外のオブジェクト、名前はまだ登録内で、呼び出し元のオブジェクトが保持されている XAML 名前スコープに呼び出したいた場合と<xref:System.Windows.FrameworkElement.RegisterName%2A>オブジェクトを定義する XAML 名前スコープにします。  
  
### <a name="xaml-namescopes-in-code"></a>コード内の XAML 名前スコープ  
 作成し、コード内の XAML 名前スコープを使用できます。 Api と XAML 名前スコープの作成に関連する概念は、純粋なコードの使用状況、に対しても同じため、XAML プロセッサに対して[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]XAML 自体を処理するときに、これらの Api と概念を使用します。 概念と API は、XAML では部分的または完全は定義された通常のオブジェクト ツリー内で名前によってオブジェクトを検索できないために主に存在します。  
  
 XAML 名前スコープを定義するオブジェクトを実装する必要があります、プログラムによって作成されたアプリケーションと読み込まれた XAML からではなく、 <xref:System.Windows.Markup.INameScope>、または、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>で XAML 名前スコープの作成をサポートするために派生したクラス、そのインスタンス。  
  
 また、読み込みおよび XAML プロセッサで処理されないを任意の要素のオブジェクトの XAML 名前スコープは作成または既定で初期化します。 明示的に名前を後で登録するその他のオブジェクトの新しい XAML 名前スコープを作成する必要があります。 XAML 名前スコープを作成するには、静的なを呼び出す<xref:System.Windows.NameScope.SetNameScope%2A>メソッドです。 としてそれを所有するオブジェクトを指定して、`dependencyObject`パラメーター、および新しい<xref:System.Windows.NameScope.%23ctor%2A>としてコンス トラクターの呼び出し、`value`パラメーター。  
  
 オブジェクト設定されている場合`dependencyObject`の<xref:System.Windows.NameScope.SetNameScope%2A>されませんが、<xref:System.Windows.Markup.INameScope>実装では、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>、呼び出し元<xref:System.Windows.FrameworkElement.RegisterName%2A>で任意の子要素は効果がありません。 新しい XAML 名前スコープを明示的に作成に失敗した場合、呼び出し<xref:System.Windows.FrameworkElement.RegisterName%2A>で例外が発生します。  
  
 コード内の XAML 名前スコープの Api を使用しての例は、次を参照してください。[名前スコープを定義する](../../../../docs/framework/wpf/graphics-multimedia/how-to-define-a-name-scope.md)です。  
  
<a name="Namescopes_in_Styles_and_Templates"></a>   
## <a name="xaml-namescopes-in-styles-and-templates"></a>スタイルとテンプレートで XAML 名前スコープ  
 スタイルおよびテンプレート[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を再利用し、簡単な方法でコンテンツを再適用する機能を提供します。 ただし、スタイルとテンプレートを含めることも要素テンプレート レベルで定義された XAML 名前。 同じテンプレートをページに複数回使用可能性があります。 このため、スタイルおよびテンプレート スタイルまたはテンプレートの適用先のオブジェクト ツリーの任意の場所の独立した独自の XAML 名前スコープを定義します。  
  
 次に例を示します。  
  
 [!code-xaml[XamlOvwSupport#NameScopeTemplates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page6.xaml#namescopetemplates)]  
  
 ここでは、同じテンプレートは、2 つの異なるボタンに適用されます。 テンプレートは、不連続の XAML 名前スコープを持っていなかった場合、`TheBorder`テンプレートで使用される名前は XAML 名前スコープで、名前の競合が発生します。 テンプレートの各インスタンスは、ため、この例の場合、各インスタンス化されたテンプレートの XAML 名前スコープに、名を正確に 1 つ含まれます、独自の XAML 名前スコープを持ちます。  
  
 スタイルは、ストーリー ボードの一部が割り当てられている特定の名前を持つことができますようにほとんどの場合も、独自の XAML 名前スコープを定義します。 これらの名前では、テンプレートをコントロールのカスタマイズの一部として再定義した場合でも、その名前を持つ要素が対象とするコントロール固有の動作が有効にします。  
  
 により、別の XAML 名前スコープ、テンプレートの名前付きの要素を検索するは、テンプレート化されていない名前を持つページ内の要素を検索するよりも難しいです。 取得することによって、テンプレートを適用したを決定する必要があります最初、<xref:System.Windows.Controls.Control.Template%2A>テンプレートが適用されているコントロールのプロパティの値。 その後のテンプレート バージョンを呼び出す<xref:System.Windows.FrameworkTemplate.FindName%2A>テンプレートが 2 番目のパラメーターとして適用された、制御を渡すことです。  
  
 コントロールの作成者は、コントロール自体で定義されている動作の対象を特定のテンプレートを適用した内の要素をという名前がここでは、規則を生成している場合を使えば、<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>コントロール実装コードからメソッドです。 <xref:System.Windows.FrameworkElement.GetTemplateChild%2A>のみコントロールの作成者へのアクセス権を持つメソッドは保護されています。  
  
 テンプレート、および、テンプレートが適用されている XAML 名前スコープを取得する必要があります内で作業する場合の値を取得<xref:System.Windows.FrameworkElement.TemplatedParent%2A>、まず<xref:System.Windows.FrameworkElement.FindName%2A>があります。 テンプレート内での作業の例になりますイベント ハンドラーの実装を記述するかどうか、適用されたテンプレート内の要素からイベントを発生させる場所。  
  
<a name="Namescopes_and_Name_related_APIs"></a>   
## <a name="xaml-namescopes-and-name-related-apis"></a>XAML 名前空間と名前に関連する Api  
 <xref:System.Windows.FrameworkElement> <xref:System.Windows.FrameworkElement.FindName%2A>、<xref:System.Windows.FrameworkElement.RegisterName%2A>と<xref:System.Windows.FrameworkElement.UnregisterName%2A>メソッドです。 これらのメソッドを呼び出すオブジェクトに、XAML 名前空間が所有している場合、メソッドは、関連する XAML 名前スコープのメソッドを呼び出します。 それ以外の場合、親要素がオンになって、XAML 名前空間を所有するいると、XAML 名前空間が見つかるまでこのプロセスは、再帰的に (動作のために、XAML プロセッサ、存在が保証されるルートにある XAML 名前スコープ)。 <xref:System.Windows.FrameworkContentElement> 例外が、類似の動作がありますをありません<xref:System.Windows.FrameworkContentElement>XAML 名前スコープを所有することです。 メソッドが上に存在<xref:System.Windows.FrameworkContentElement>呼び出しを最終的に転送できるように、<xref:System.Windows.FrameworkElement>親要素です。  
  
 <xref:System.Windows.NameScope.SetNameScope%2A> 既存のオブジェクトに新しい XAML 名前スコープをマップに使用されます。 呼び出すことができます<xref:System.Windows.NameScope.SetNameScope%2A>も複数回リセットまたは XAML をオフにするためにスコープがするではありません一般的な使用方法です。 また、<xref:System.Windows.NameScope.GetNameScope%2A>コードからは通常使用されません。  
  
### <a name="xaml-namescope-implementations"></a>XAML 名前スコープの実装  
 次のクラスを実装<xref:System.Windows.Markup.INameScope>直接。  
  
-   <xref:System.Windows.NameScope>  
  
-   <xref:System.Windows.Style>  
  
-   <xref:System.Windows.ResourceDictionary>  
  
-   <xref:System.Windows.FrameworkTemplate>  
  
 <xref:System.Windows.ResourceDictionary> XAML の名前や名前スコープ; を使用しません。使用してキー代わりに、ディクショナリの実装になっているためです。 唯一の理由<xref:System.Windows.ResourceDictionary>実装<xref:System.Windows.Markup.INameScope>true XAML 名前スコープの違いをわかりやすくユーザー コードに例外が発生にできるようにする方法とは、<xref:System.Windows.ResourceDictionary>キーを処理および XAML 名前スコープに適用されなかったことを確実にも、<xref:System.Windows.ResourceDictionary>親要素です。  
  
 <xref:System.Windows.FrameworkTemplate> および<xref:System.Windows.Style>実装<xref:System.Windows.Markup.INameScope>明示的なインターフェイスの定義を使用します。 明示的な実装を介してアクセスされるときに通常の動作にこれらの XAML 名前スコープを許可する、<xref:System.Windows.Markup.INameScope>インターフェイスは XAML 名前スコープが伝達される方法で[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]内部プロセスです。 明示的なインターフェイスの定義がの従来の API サーフェイスの一部ではないが、<xref:System.Windows.FrameworkTemplate>と<xref:System.Windows.Style>頻度の低いを呼び出す必要があるため、<xref:System.Windows.Markup.INameScope>メソッド<xref:System.Windows.FrameworkTemplate>と<xref:System.Windows.Style>はその他の API を使用して直接、または代わりにように<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>です。  
  
 次のクラスを使用して、独自の XAML 名前スコープを定義する、<xref:System.Windows.NameScope?displayProperty=nameWithType>ヘルパー クラスおよびその XAML 名前スコープの実装を通じてへの接続、<xref:System.Windows.NameScope.NameScope%2A?displayProperty=nameWithType>添付プロパティ。  
  
-   <xref:System.Windows.FrameworkElement>  
  
-   <xref:System.Windows.FrameworkContentElement>  
  
## <a name="see-also"></a>関連項目  
 [XAML 名前空間および WPF XAML の名前空間の割り当て](../../../../docs/framework/wpf/advanced/xaml-namespaces-and-namespace-mapping-for-wpf-xaml.md)  
 [x:Name ディレクティブ](../../../../docs/framework/xaml-services/x-name-directive.md)
