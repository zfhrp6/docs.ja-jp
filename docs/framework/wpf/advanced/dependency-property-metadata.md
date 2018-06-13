---
title: 依存関係プロパティのメタデータ
ms.date: 03/30/2017
helpviewer_keywords:
- APIs [WPF], metadata
- dependency properties [WPF], metadata
- metadata [WPF], for dependency properties
- overriding metadata [WPF]
ms.assetid: d01ed009-b722-41bf-b82f-fe1a8cdc50dd
ms.openlocfilehash: f0aa1d2962b0bccea7a0901877b29550319aaa3f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541698"
---
# <a name="dependency-property-metadata"></a>依存関係プロパティのメタデータ
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] プロパティ システムには、リフレクションや一般的な [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 特性から得られる以上の詳細なプロパティ情報を提供するメタデータ報告システムがあります。 依存関係プロパティのメタデータは、依存関係プロパティを定義するクラスで個別に割り当てることも、依存関係プロパティを別のクラスに追加する際に変更することもできます。また、依存関係プロパティをその定義元の基本クラスから継承するすべての派生クラスで明確にオーバーライドすることもできます。  
  
 
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、ユーザーが [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] クラスの既存の依存関係プロパティの使用という観点から依存関係プロパティを理解し、「[依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)」トピックを通読していることを前提としています。 このトピックの例を理解するには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] について理解し、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アプリケーションの作成方法に精通している必要があります。  
  
<a name="dp_metadata_contents"></a>   
## <a name="how-dependency-property-metadata-is-used"></a>依存関係プロパティのメタデータの使用方法  
 依存関係プロパティのメタデータは、依存プロパティの特性を照会して調べるためのオブジェクトとして存在します。 また、このメタデータは、特定の依存関係プロパティを処理するために、プロパティ システムによって頻繁にアクセスされます。 依存関係プロパティのメタデータ オブジェクトには、次のような情報が格納されます。  
  
-   依存関係プロパティの既定値 (ローカル値、スタイル、継承などによってその他の依存関係プロパティ値が指定されない場合)。依存関係プロパティの値を割り当てる際の、既定値と、プロパティ システムで使用される優先順位の関係に関する詳細な説明については、「[依存関係プロパティ値の優先順位](../../../../docs/framework/wpf/advanced/dependency-property-value-precedence.md)」を参照してください。  
  
-   所有者型に基づく強制型変換または変更通知の動作に影響を与えるコールバック実装への参照。 多くの場合、これらのコールバックは非パブリックなアクセス レベルで定義されます。したがって、参照が、許可されたアクセス スコープ内にない限り、一般にメタデータから実際の参照を取得することはできません。 依存関係プロパティのコールバックの詳細については、「[依存関係プロパティのコールバックと検証](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)」を参照してください。  
  
-   対象の依存関係プロパティが WPF フレームワーク レベルのプロパティと見なされる場合、WPF フレームワーク レベルの依存関係プロパティ特性がメタデータに含まれる可能性があります。これは、WPF フレームワーク レベルのレイアウト エンジンやプロパティ継承ロジックなどのサービスの情報および状態を報告します。 この内容に関する依存関係プロパティのメタデータの詳細については、「[フレームワーク プロパティ メタデータ](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)」を参照してください。  
  
<a name="APIs"></a>   
## <a name="metadata-apis"></a>メタデータ API  
 ほとんどのプロパティのシステムで使用されるメタデータ情報を報告する型が、<xref:System.Windows.PropertyMetadata>クラスです。 メタデータ インスタンスは、依存関係プロパティをプロパティ システムに登録する際に必要に応じて指定されます。それ自体を所有者として追加する追加の型、または基本クラスの依存関係プロパティ定義から継承したメタデータをオーバーライドする追加の型に再度指定することもできます。 (プロパティの登録がメタデータを既定値を指定しない場合の<xref:System.Windows.PropertyMetadata>がそのクラスの既定値で作成します)。として登録されているメタデータが返される<xref:System.Windows.PropertyMetadata>を呼び出すと、さまざまな<xref:System.Windows.DependencyProperty.GetMetadata%2A>で依存関係プロパティのメタデータを取得するオーバー ロード、<xref:System.Windows.DependencyObject>インスタンス。  
  
 <xref:System.Windows.PropertyMetadata>アーキテクチャ部門 WPF フレームワーク レベルのクラスなどのより詳細なメタデータを提供する、クラスはから導き出されます。 <xref:System.Windows.UIPropertyMetadata> アニメーションがレポートを追加し、<xref:System.Windows.FrameworkPropertyMetadata>前のセクションに記載されている WPF フレームワーク レベルのプロパティを提供します。 依存関係プロパティが登録されると、これらを登録できます<xref:System.Windows.PropertyMetadata>クラスを派生します。 メタデータを調べるときに、基本<xref:System.Windows.PropertyMetadata>より特定のプロパティを確認するように、型を派生クラスにキャスト可能性があることができます。  
  
> [!NOTE]
>  指定できるプロパティの特性<xref:System.Windows.FrameworkPropertyMetadata>"flags"としては、このドキュメントで呼ばします。 フラグの列挙を使用してこれらの値を指定した依存関係プロパティの登録で使用するための新しいメタデータ インスタンスに作成するか、メタデータ オーバーライド、 <xref:System.Windows.FrameworkPropertyMetadataOptions> に列挙型の可能性のある連結された値を指定し、<xref:System.Windows.FrameworkPropertyMetadata>コンス トラクターです。 ただし、これを構築すると、これらのオプションの特性が内で公開された、<xref:System.Windows.FrameworkPropertyMetadata>として一連の構築の列挙値ではなくブール型プロパティです。 これらのブール型プロパティを使用すると、目的の情報を取得するためにフラグ列挙値に対してマスクを適用することなく、各条件をチェックすることができます。 コンス トラクターを使用して連結された<xref:System.Windows.FrameworkPropertyMetadataOptions>コンス トラクター シグネチャの長さを実際の構築されたメタデータ プロパティを公開します不連続より直観的なメタデータをクエリするために対し、適切で保持するためにします。  
  
<a name="override_or_subclass"></a>   
## <a name="when-to-override-metadata-when-to-derive-a-class"></a>メタデータをオーバーライドする場合、クラスを派生する場合  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムには、依存関係プロパティを完全に再実装することなく、依存関係プロパティの一部の特性を変更するための機能が用意されています。 これは、特定の型に存在する依存関係プロパティについて、そのプロパティ メタデータの別のインスタンスを構築することで実現されます。 既存の依存関係プロパティの大部分は仮想プロパティではありません。したがって、厳密には、継承クラスでの依存関係プロパティの "再実装" は、既存のメンバーをシャドウすることによってのみ実現されます。  
  
 型の依存関係プロパティに対して有効にしようとしているシナリオが、既存の依存関係プロパティの特性の変更では実現できない場合、派生クラスを作成し、その派生クラスでカスタム依存関係プロパティを宣言することが必要になる場合があります。 カスタム依存関係プロパティは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA#tla_api#plural](../../../../includes/tlasharptla-apisharpplural-md.md)] で定義されている依存関係プロパティとまったく同じように動作します。 カスタム依存関係プロパティの詳細については、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」を参照してください。  
  
 オーバーライドすることができない依存関係プロパティの代表的な特性の 1 つは、依存関係プロパティの値型です。 目的の動作にほぼ合致する依存関係プロパティを継承していても、その依存関係プロパティに別の型が必要な場合には、カスタム依存関係プロパティを実装し、型変換またはカスタム クラスのその他の実装を通じてプロパティをリンクする必要があります。 またを置き換えることはできません、既存<xref:System.Windows.ValidateValueCallback>登録フィールド自体では、メタデータ内ではなく、このコールバックが存在するため、します。  
  
<a name="scenarios"></a>   
## <a name="scenarios-for-changing-existing-metadata"></a>既存のメタデータを変更するシナリオ  
 既存の依存関係プロパティのメタデータを使用している場合、依存関係プロパティのメタデータを変更する一般的なシナリオの 1 つは、既定値を変更することです。 プロパティ システム コールバックの変更または追加は、より高度なシナリオです。 これは、実装している派生クラスの相互関係が依存関係プロパティごとに異なる場合に使用します。 コードと宣言的な使用方法の両方をサポートするプログラミング モデルを使用する条件の 1 つとして、プロパティを任意の順序で設定できる必要があります。 したがって、依存関係プロパティはすべて、コンテキストを使用せずに Just-In-Time で設定する必要があります。また、設定順序 (コンストラクター内の順序など) に依存することもできません。 この内容に関するプロパティ システムの詳細については、「[依存関係プロパティのコールバックと検証](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)」を参照してください。 検証コールバックは、メタデータの一部ではなく、依存関係プロパティ識別子の一部であることに注意してください。 したがって、検証コールバックは、メタデータのオーバーライドでは変更できません。  
  
 既存の依存関係プロパティに対して、WPF フレームワーク レベルのプロパティのメタデータ オプションの変更が必要になる場合があります。 これらのオプションは、WPF フレームワーク レベルのプロパティに関する特定の既知の条件を、レイアウト システムなどの他の WPF フレームワーク レベルのプロセスに伝達します。  新しい依存関係プロパティを登録する場合にのみ、通常実行はオプションの設定がの一部として、WPF フレームワーク レベルのプロパティ メタデータを変更することも、<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>または<xref:System.Windows.DependencyProperty.AddOwner%2A>呼び出します。 使用する具体的な値および詳細については、「[フレームワーク プロパティ メタデータ](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)」を参照してください。 新しく登録した依存関係プロパティに対してこれらのオプションを設定する方法の詳細については、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」を参照してください。  
  
<a name="dp_override_metadata"></a>   
### <a name="overriding-metadata"></a>メタデータのオーバーライド  
 メタデータのオーバーライドの主な目的は、型に存在する依存関係プロパティに適用される、メタデータから派生したさまざまな動作を変更できるようにすることです。 この理由については、「[メタデータ](#dp_metadata_contents)」セクションで詳しく説明します。 コード例を含む詳細については、「[方法 : 依存関係プロパティのメタデータをオーバーライドする](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md)」を参照してください。  
  
 登録の呼び出し中に、依存関係プロパティのプロパティのメタデータを指定することができます (<xref:System.Windows.DependencyProperty.Register%2A>)。 ただし、多くの場合、その依存関係プロパティを継承するクラスに対して、型固有のメタデータを提供する必要があります。 呼び出すことによってこれを行う、<xref:System.Windows.DependencyProperty.OverrideMetadata%2A>メソッドです。  例については、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)]、<xref:System.Windows.FrameworkElement>クラスは、最初に登録する型、<xref:System.Windows.UIElement.Focusable%2A>依存関係プロパティです。 <xref:System.Windows.Controls.Control>クラスからそれを変更する、独自の既定の初期値を指定する依存関係プロパティのメタデータをオーバーライドする`false`に`true`、それ以外の場合、元に再使用と<xref:System.Windows.UIElement.Focusable%2A>実装します。  
  
 メタデータをオーバーライドすると、さまざまなメタデータ特性がマージされるか置き換えられます。  
  
-   <xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A> マージされています。 新しく追加した場合<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>、そのコールバックがメタデータに格納します。 指定しない場合、<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>の値よりも優先的に<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>がメタデータに指定する、最も近い先祖から参照として昇格します。  
  
-   実際のプロパティのシステム動作<xref:System.Windows.PropertyMetadata.PropertyChangedCallback%2A>は、階層内のすべてのメタデータ所有者の実装が保持され、テーブルに追加、プロパティのシステムでの実行の順序としていること、最派生クラスのコールバックが最初に呼び出されます。  
  
-   <xref:System.Windows.PropertyMetadata.DefaultValue%2A> 置換されます。 指定しない場合、<xref:System.Windows.PropertyMetadata.DefaultValue%2A>の値よりも優先的に<xref:System.Windows.PropertyMetadata.DefaultValue%2A>はメタデータに指定する、最も近い先祖から取得します。  
  
-   <xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A> 実装は置き換えられます。 新しく追加した場合<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>、そのコールバックがメタデータに格納します。 指定しない場合、<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>の値よりも優先的に<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>がメタデータに指定する、最も近い先祖から参照として昇格します。  
  
-   プロパティのシステム動作はのみですが、<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>即時のメタデータでが呼び出されます。 他の参照がありません<xref:System.Windows.PropertyMetadata.CoerceValueCallback%2A>階層内の実装が保持されます。  
  
 この動作はによって実装<xref:System.Windows.PropertyMetadata.Merge%2A>、およびメタデータの派生クラスでオーバーライドできます。  
  
#### <a name="overriding-attached-property-metadata"></a>添付プロパティのメタデータのオーバーライド  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、添付プロパティは依存関係プロパティとして実装されます。 このことは、添付プロパティもプロパティ メタデータを持ち、これを個々のクラスでオーバーライドできることを意味します。 内の添付プロパティのスコープに関する考慮事項[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は通常を<xref:System.Windows.DependencyObject>添付プロパティが設定を持つことができます。 そのため、いずれか<xref:System.Windows.DependencyObject>ように、クラスのインスタンスに設定する必要があります、派生クラスは、添付プロパティのメタデータをオーバーライドできます。 オーバーライドできるのは、既定値、コールバック、または WPF フレームワーク レベルの特性報告プロパティです。 添付プロパティがクラスのインスタンスで設定されている場合、そのオーバーライド プロパティ メタデータ特性が適用されます。 たとえば、プロパティが他では特に指定されていないときには、オーバーライド値がクラスのインスタンス上の添付プロパティの値として報告されるように、既定値をオーバーライドできます。  
  
> [!NOTE]
>  <xref:System.Windows.FrameworkPropertyMetadata.Inherits%2A>添付プロパティのプロパティは無効です。  
  
<a name="dp_add_owner"></a>   
### <a name="adding-a-class-as-an-owner-of-an-existing-dependency-property"></a>既存の依存関係プロパティの所有者としてのクラスの追加  
 クラスを使用して、既に登録されている依存関係プロパティの所有者として追加できます、<xref:System.Windows.DependencyProperty.AddOwner%2A>メソッドです。 これにより、当初は別の型に対して登録された依存関係プロパティをクラスで使用できるようになります。 通常、追加するクラスは、所有者としてその依存関係プロパティを最初に登録した型の派生クラスではありません。 これにより、元の所有者クラスと追加するクラスが同一のクラス階層内にない場合でも、クラスとその派生クラスで依存関係プロパティの実装を "継承" することが事実上可能になります。 また、追加するクラスとすべての派生クラスでは、型固有のメタデータを元の依存関係プロパティに提供することができます。  
  
 追加するクラスは、プロパティ システムのユーティリティ メソッドを介してそれ自体を所有者として追加するだけでなく、追加のパブリック メンバーをそれ自体で宣言する必要があります。これは、依存関係プロパティを完全な形でプロパティ システムに登録し、コードとマークアップの両方に対して公開するためです。 既存の依存関係プロパティを追加するクラスは、その依存関係プロパティのオブジェクト モデルを公開する限り、新しいカスタム依存関係プロパティを定義するクラスと同様の役割を負います。 これらのメンバーの中で最初に公開するのは、依存関係プロパティの識別子フィールドです。 このフィールドにする必要があります、`public static readonly`型のフィールド<xref:System.Windows.DependencyProperty>の戻り値に割り当てられる、<xref:System.Windows.DependencyProperty.AddOwner%2A>呼び出します。 2 番目に定義するメンバーは、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] の "ラッパー" プロパティです。 ラッパーが容易にコードで、依存関係プロパティを操作する (呼び出しを避けるため<xref:System.Windows.DependencyObject.SetValue%2A>各時間、およびラッパー自体でその呼び出しを 1 回だけを実行することができます)。 このラッパーの実装方法は、カスタム依存関係プロパティを登録する場合の実装方法とまったく同じです。 依存関係プロパティの実装の詳細については、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」および「[依存関係プロパティの所有者の種類を追加する](../../../../docs/framework/wpf/advanced/how-to-add-an-owner-type-for-a-dependency-property.md)」を参照してください。  
  
#### <a name="addowner-and-attached-properties"></a>AddOwner および添付プロパティ  
 呼び出すことができます<xref:System.Windows.DependencyProperty.AddOwner%2A>依存関係プロパティの添付プロパティの所有者のクラスによって定義されます。 通常、これは、以前の添付プロパティを非添付の依存関係プロパティとして公開する目的で行います。 公開は、<xref:System.Windows.DependencyProperty.AddOwner%2A>として値を返す、`public static readonly`依存関係プロパティの識別子として使用するためのフィールドし、プロパティは、メンバー テーブルが表示され、非添付プロパティをサポートするように、適切な「ラッパー」プロパティを定義しますクラスの使用率。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.PropertyMetadata>  
 <xref:System.Windows.DependencyObject>  
 <xref:System.Windows.DependencyProperty>  
 <xref:System.Windows.DependencyProperty.GetMetadata%2A>  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [フレームワーク プロパティ メタデータ](../../../../docs/framework/wpf/advanced/framework-property-metadata.md)
