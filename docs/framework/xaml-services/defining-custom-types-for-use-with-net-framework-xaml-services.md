---
title: "Defining Custom Types for Use with .NET Framework XAML Services | Microsoft Docs"
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
  - "defining custom types [XAML Services]"
ms.assetid: c2667cbd-2f46-4a7f-9dfc-53696e35e8e4
caps.latest.revision: 11
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 11
---
# Defining Custom Types for Use with .NET Framework XAML Services
ビジネス オブジェクトに相当するカスタム型を定義する場合や、特定のフレームワークに依存しない型を定義する場合にも、XAML のベスト プラクティスに従って確実に対応できます。  このベスト プラクティスに従った場合、.NET Framework XAML サービスとその XAML リーダーおよび XAML ライターでは、型の XAML 特性を検出し、XAML 型システムに基づいて XAML ノード ストリームで適切に表現できます。  ここでは、型定義のベスト プラクティスと、型またはメンバーの CLR 属性の設定について説明します。  
  
## XAML のコンストラクター パターンと型定義  
 XAML でカスタム クラスをオブジェクト要素としてインスタンス化できるようにするには、次の要件が満たされている必要があります。  
  
-   カスタム クラスがパブリックであり、既定の \(パラメーターなしの\) パブリック コンストラクターが公開されている必要がある。  \(構造体に関する説明は次のセクションを参照してください\)。  
  
-   カスタム クラスが入れ子になっていない。  完全パス名に "ドット" を追加すると、クラスと名前空間の区分があいまいになり、添付プロパティなど、他の XAML 機能に干渉します。  
  
 オブジェクトをオブジェクト要素としてインスタンス化できる場合、作成したオブジェクトで、そのオブジェクトを基になる型として受け取る任意のプロパティのプロパティ要素形式を読み込むことができます。  
  
 値コンバーターを有効にした場合、これらの条件を満たしていない型のオブジェクト値を指定できます。  詳細については、「[Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)」を参照してください。  
  
### 構造体  
 構造体は常に CLR 定義に基づいて XAML で構築できます。  これは、CLR コンパイラによって構造体の既定のコンストラクターが暗黙的に作成されることに起因します。  このコンストラクターは、すべてのプロパティ値を既定値に初期化します。  
  
 構造体の既定のコンストラクターの動作が望ましくない場合もあります。  これは、構造体が値の入力を目的として、概念上は共用体として機能することに起因すると考えられます。  共用体では、格納されている値は同時には解釈されず、結果として、そのプロパティを設定できなくなる可能性があります。  WPF の語彙では、このような構造体の例に該当するのは <xref:System.Windows.GridLength> です。  このような構造体には、型コンバーターを実装して、構造体の値の異なる解釈やモードを設定する文字列の規則に基づき、値を属性形式で表示できるようにする必要があります。  この構造体では、コード構築が既定以外のコンストラクターによって行われる場合にも、同じ動作が見られると考えられます。  
  
### インターフェイス  
 インターフェイスは、メンバーの基になる型として使用できます。  XAML 型システムでは、割り当て可能なリストがチェックされ、値として提供されたオブジェクトをインターフェイスに割り当てできると想定しています。  関連する割り当て可能な型で XAML の作成要件がサポートされている限り、インターフェイスを XAML 型として表現する方法を考慮する必要はありません。  
  
### ファクトリ メソッド  
 ファクトリ メソッドは XAML 2009 の機能であり、  オブジェクトには既定のコンストラクターを設定する必要があるという XAML の原則に修正を加えます。  ここでは、ファクトリ メソッドの詳細については説明しません。  「[x:FactoryMethod Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md)」を参照してください。  
  
## 列挙型  
 列挙型には、XAML のネイティブ型変換の動作が設定されています。  XAML で指定した列挙定数の名前は、基になる列挙型に対して解決され、列挙値が XAML オブジェクト ライターに返されます。  
  
 XAML では、<xref:System.FlagsAttribute> を適用した列挙型のフラグ スタイルの使用方法をサポートしています。  詳細については、「[XAML 構文の詳細](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)」を参照してください   \(「[XAML 構文の詳細](../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)」は WPF のユーザー向けに記述されていますが、このトピックの情報のほとんどは XAML に関連しており、特定の実装フレームワークには依存していません\)。  
  
## メンバー定義  
 型では、XAML の使用方法のメンバーを定義できます。  特定の型が XAML 対応でない場合でも、型で XAML 対応のメンバーを定義できます。  これは、CLR の継承によって可能になります。  メンバーを継承する一部の型で型としての XAML の使用方法をサポートし、基になる型の XAML の使用方法をそのメンバーがサポートしているか、そのメンバーでネイティブな XAML 構文を使用できる限り、そのメンバーは XAML 対応のメンバーです。  
  
### プロパティ  
 一般的な CLR `get` アクセサー パターンと `set` アクセサー パターン、および言語に応じたキーワードを使用してプロパティをパブリックな CLR プロパティとして定義する場合、XAML 型システムでは、<xref:System.Xaml.XamlMember.IsReadPublic%2A> や <xref:System.Xaml.XamlMember.IsWritePublic%2A> など、<xref:System.Xaml.XamlMember> プロパティに提供された適切な情報により、プロパティをメンバーとして報告できます。  
  
 特定のプロパティでは、<xref:System.ComponentModel.TypeConverterAttribute> を適用することで、テキスト構文を有効にできます。  詳細については、「[Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)」を参照してください。  
  
 テキスト構文やネイティブな XAML 変換が存在せず、マークアップ拡張機能の使用などの間接指定も存在しない場合、プロパティの型 \(XAML 型システムでは <xref:System.Xaml.XamlMember.TargetType%2A>\) でターゲット型を CLR 型として扱うことで、XAML オブジェクト ライターにインスタンスを返すことができる必要があります。  
  
 XAML 2009 を使用する場合、前述の項目が考慮されていない状況でも、型定義よりも使用方法に問題があるときは、値を提供する目的で [x:Reference Markup Extension](../../../docs/framework/xaml-services/x-reference-markup-extension.md) を使用できます。  
  
### イベント  
 パブリックな CLR イベントとしてイベントを定義する場合、XAML 型システムでは、<xref:System.Xaml.XamlMember.IsEvent%2A> を `true` に設定して、イベントをメンバーとして報告できます。  イベント ハンドラーの記述は .NET Framework XAML サービスの機能の範囲外であり、特定のフレームワークや実装で行われます。  
  
### メソッド  
 メソッドのインライン コードは、既定の XAML 機能ではありません。  ほとんどの場合、XAML からメンバーを直接参照することはなく、XAML でのメソッドの役割は特定の XAML パターンに対するサポートを提供することに限定されます。  [x:FactoryMethod Directive](../../../docs/framework/xaml-services/x-factorymethod-directive.md) は例外です。  
  
### フィールド  
 CLR の設計ガイドラインでは、非静的フィールドは推奨されていません。  静的フィールドでは、[x:Static Markup Extension](../../../docs/framework/xaml-services/x-static-markup-extension.md) を介した場合にのみ、静的フィールド値にアクセスできます。この場合、[x:Static](../../../docs/framework/xaml-services/x-static-markup-extension.md) の使用に対してフィールドを公開するために、CLR の定義で特別な対応を行う必要はありません。  
  
## アタッチ可能なメンバー  
 アタッチ可能なメンバーは、定義元の型のアクセサー メソッド パターンを介して XAML に公開されます。  定義元の型自体は、XAML 対応のオブジェクトである必要はありません。  実際には、アタッチ可能なメンバーを所有し、関連の動作を実装するが、UI 表現などのその他の機能を提供しないサービス クラスを宣言するというのが一般的なパターンです。  以降では、プレースホルダー *PropertyName* は、アタッチ可能なメンバーの名前を表します。  この名前は、[XamlName の文法](../../../docs/framework/xaml-services/xamlname-grammar.md) で有効である必要があります。  
  
 型の各パターンおよびその他のメソッドの間では、名前の衝突に注意してください。  いずれかのパターンに一致するメンバーが存在する場合、開発者の意図に関係なく、XAML プロセッサによってアタッチ可能なメンバーの使用経路として解釈される場合があります。  
  
#### GetPropertyName アクセサー  
 `Get` *PropertyName* アクセサーのシグネチャの形式は次のとおりです。  
  
 `public static object Get` *PropertyName* `(object`  `target` `)`  
  
-   `target` オブジェクトは、実装内で具体的な型として指定できます。  これにより、アタッチ可能なメンバーの使用方法にスコープを設定できます。意図したスコープ外の使用方法では無効なキャスト例外がスローされ、XAML 解析エラーとして通知されます。  パラメーター名 `target` は必須ではありませんが、ほとんどの実装で慣例により、`target` という名前が付けられます。  
  
-   戻り値は、実装内で具体的な型として指定できます。  
  
 アタッチ可能なメンバーの属性の使用方法で <xref:System.ComponentModel.TypeConverter> 対応のテキスト構文をサポートするには、<xref:System.ComponentModel.TypeConverterAttribute> を `Get`*PropertyName* アクセサーに適用します。  `set` ではなく `get` に適用する方法では、複雑になる場合があります。ただし、この規則では、シリアル化に対応する読み取り専用のアタッチ可能なメンバーをサポートできるので、デザイナーのシナリオによっては役立つ場合があります。  
  
#### SetPropertyName アクセサー  
 Set*PropertyName* アクセサーのシグネチャの形式は次のとおりです。  
  
 `public static void Set` *PropertyName* `(object`  `target` `, object`  `value` `)`  
  
-   `target` オブジェクトは、前のセクションで説明した同じロジックと結果に基づいて、実際の実装ではさらに詳細な型として指定できます。  
  
-   `value` オブジェクトは、実装の中で具体的な型として指定できます。  
  
 このメソッドの値は、XAML の使用方法から派生した、通常は属性形式の入力であることに注意してください。  属性形式では、テキスト構文に対する値コンバーターのサポートが必要であり、`Get`*PropertyName* アクセサーに属性を追加します。  
  
### アタッチ可能なメンバー ストア  
 アクセサー メソッドは、一般に、アタッチ可能なメンバー値をオブジェクト グラフに配置したり、オブジェクト グラフから値を取得して適切にシリアル化したりする手段としては、十分ではありません。  この機能を提供するには、前のアクセサー シグネチャの `target` オブジェクトが値を格納できる必要があります。  ストレージ機構は、アタッチ可能なメンバーの原則 \(アタッチ可能なメンバーがメンバー リストに含まれていないターゲットに、メンバーをアタッチできる\) に準拠している必要があります。  .NET Framework XAML サービスでは、API の <xref:System.Xaml.IAttachedPropertyStore> と <xref:System.Xaml.AttachablePropertyServices> を使用して、アタッチ可能なメンバー ストアの実装手法を利用できます。  <xref:System.Xaml.IAttachedPropertyStore> は、XAML ライターがストアの実装を検出するために使用します。これは、アクセサーの `target` に相当する型で実装する必要があります。  静的 <xref:System.Xaml.AttachablePropertyServices> API は、アクセサーの本体で使用され、アタッチ可能なメンバーをその <xref:System.Xaml.AttachableMemberIdentifier> で参照します。  
  
## XAML 関連の CLR 属性  
 XAML 型システム情報を .NET Framework XAML サービスに報告するために、型、メンバー、およびアセンブリに属性を適切に設定することが重要です。  これは、.NET Framework XAML サービスの XAML リーダーおよび XAML ライターにより直接 XAML システムで型を使用する場合と、同じく XAML リーダーおよび XAML ライターにより XAML でフレームワークを定義または使用する場合のどちらにも関連します。  
  
 カスタム型の XAML サポートに関連する XAML 関連の各属性のリストについては、「[XAML\-Related CLR Attributes for Custom Types and Libraries](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)」を参照してください。  
  
## 使用方法  
 カスタム型を使用する場合、マークアップ作成者がアセンブリのプレフィックスと、カスタム型を含む CLR 名前空間をマッピングする必要があります。  ここでは、その具体的な手順については説明しません。  
  
## アクセス レベル  
 XAML では、アクセス レベルが `internal` である型を読み込んでインスタンス化できます。  この機能は、ユーザー コードで独自の型を定義し、同じユーザー コード スコープの一部でもあるマークアップからこれらのクラスをインスタンス化できるようにするためのものです。  
  
 WPF では、アクセス レベルが `public` であるサポート クラスの宣言によって暗示される可能性のある拡張機構の一部としてではなく、UI 動作をリファクタリングするための <xref:System.Windows.Controls.UserControl> をユーザー コードで定義します。  こうした <xref:System.Windows.Controls.UserControl> は、バッキング コードが同じアセンブリ \(ここから XAML 型として参照\) にコンパイルされる場合は `internal` アクセスを使用して宣言できます。  
  
 完全な信頼で XAML を読み込み、<xref:System.Xaml.XamlObjectWriter> を使用するアプリケーションの場合、アクセス レベルが `internal` であるクラスの読み込みは常に有効です。  
  
 部分信頼で XAML を読み込むアプリケーションの場合は、<xref:System.Xaml.Permissions.XamlAccessLevel> API を使用してアクセス レベルの特性を制御できます。  また、遅延機構 \(WPF テンプレート システムなど\) は、アクセス レベルのアクセス許可を反映し、それを最終的な実行時の評価のために保持できる必要があります。これは、<xref:System.Xaml.Permissions.XamlAccessLevel> 情報を渡すことによって内部で処理されます。  
  
### WPF 実装  
 BAML が部分信頼で読み込まれ、BAML ソースに相当するアセンブリに対してアクセスが <xref:System.Xaml.Permissions.XamlAccessLevel.AssemblyAccessTo%2A> に制限されている場合、WPF XAML では、部分信頼のアクセス モデルが使用されます。  遅延のために、WPF ではアクセス レベル情報を渡す機構として <xref:System.Xaml.IXamlObjectWriterFactory.GetParentSettings%2A?displayProperty=fullName> を使用します。  
  
 WPF XAML の用語では、*内部型*とは参照元の XAML も含む同じアセンブリによって定義される型のことを表します。  こうした型は、マッピングの assembly\= の部分を意図的に省略した XAML 名前空間を通じてマッピングできます \(例: `xmlns:local="clr-namespace:WPFApplication1"`\)。  BAML が内部型を参照し、その型のアクセス レベルが `internal` である場合は、アセンブリに対して `GeneratedInternalTypeHelper` クラスが生成されます。  `GeneratedInternalTypeHelper` を避けるには、`public` アクセス レベルを使用するか、該当するクラスを別個のアセンブリにファクタリングして、そのアセンブリを依存させる必要があります。  
  
## 参照  
 [XAML\-Related CLR Attributes for Custom Types and Libraries](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md)   
 [XAML Services](../../../docs/framework/xaml-services/index.md)