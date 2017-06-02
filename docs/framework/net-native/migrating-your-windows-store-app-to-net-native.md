---
title: "Windows ストア アプリの .NET ネイティブへの移行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
caps.latest.revision: 29
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 29
---
# Windows ストア アプリの .NET ネイティブへの移行
[!INCLUDE[net_native](../../../includes/net-native-md.md)]は、Windows ストアまたは開発者のコンピューターでアプリの静的なコンパイルを行います。 これは、デバイス上で Just\-In\-Time \(JIT\) コンパイラまたは[ネイティブ イメージ ジェネレーター \(Ngen.exe\)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) によって Windows ストア アプリに対して実行される動的なコンパイルとは異なります。 違いはありますが、[!INCLUDE[net_native](../../../includes/net-native-md.md)] は [Windows ストア アプリ用 .NET](http://msdn.microsoft.com/library/windows/apps/br230302.aspx) との互換性を保持しようとします。 Windows ストア アプリ用 .NET で機能する大部分が [!INCLUDE[net_native](../../../includes/net-native-md.md)]でも機能します。  ただし、動作に違いがある場合もあります。 このドキュメントでは、次の領域における、標準の Windows ストア アプリ用 .NET と [!INCLUDE[net_native](../../../includes/net-native-md.md)]との違いについて説明します。  
  
-   [全般的なランタイムの違い](#Runtime)  
  
-   [動的プログラミングの違い](#Dynamic)  
  
-   [リフレクションに関するその他の違い](#Reflection)  
  
-   [サポートされていないシナリオと API](#Unsupported)  
  
-   [Visual Studio の違い](#VS)  
  
<a name="Runtime"></a>   
## 全般的なランタイムの違い  
  
-   アプリが共通言語ランタイム \(CLR\) で実行されているときに JIT コンパイラによってスローされる <xref:System.TypeLoadException> などの例外は、通常、[!INCLUDE[net_native](../../../includes/net-native-md.md)]によって処理されるときにはコンパイル時エラーになります。  
  
-   アプリの UI スレッドから <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=fullName> メソッドを呼び出さないでください。 これにより [!INCLUDE[net_native](../../../includes/net-native-md.md)]でデッドロックが発生する可能性があります。  
  
-   静的クラス コンストラクターの呼び出し順序に依存しないでください。[!INCLUDE[net_native](../../../includes/net-native-md.md)]では、呼び出し順序が標準ランタイムでの順序と異なります。 \(標準ランタイムを使用する場合であっても、静的クラス コンストラクターの実行順序に依存しないでください。\)  
  
-   スレッドでの呼び出しを行わない無限ループ \(たとえば、`while(true);`\) によって、アプリが停止する可能性があります。 同様に、長時間または無限の待機によってもアプリが停止する可能性があります。  
  
-   特定の汎用初期化サイクルは、[!INCLUDE[net_native](../../../includes/net-native-md.md)]で例外をスローしません。 たとえば、次のコードは標準 CLR では <xref:System.TypeLoadException> 例外をスローします。[!INCLUDE[net_native](../../../includes/net-native-md.md)]ではスローしません。  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   場合によっては、[!INCLUDE[net_native](../../../includes/net-native-md.md)]は、.NET Framework クラス ライブラリのさまざまな実装を提供します。 メソッドから返されるオブジェクトは、常に、返される型のメンバーを実装します。 ただし、その補助的な実装が異なるため、その他の .NET Framework プラットフォームの場合と同じ型セットへのオブジェクトのキャストを行うことができない場合があります。 たとえば、<xref:System.Collections.Generic.IEnumerable%601> や <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=fullName> などのメソッドにより返される <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=fullName> インターフェイス オブジェクトを `T[]` にキャストできない場合があります。  
  
-   WinInet キャッシュは、Windows ストア アプリ用 .NET では既定で有効になっていませんが、[!INCLUDE[net_native](../../../includes/net-native-md.md)]では有効になっています。 これによりパフォーマンスが向上しますが、作業セットへの影響があります。 開発者のアクションは必要ありません。  
  
<a name="Dynamic"></a>   
## 動的プログラミングの違い  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]は、パフォーマンスを最大化するために、.NET Framework のコードに静的にリンクし、アプリにローカルなコードにします。 ただし、バイナリ サイズは小さいままである必要があるため、.NET Framework 全体を取り入れることはできません。[!INCLUDE[net_native](../../../includes/net-native-md.md)] コンパイラは、未使用のコードへの参照を削除する依存関係レジューサを使用して、この制限を解決します。 ただし、[!INCLUDE[net_native](../../../includes/net-native-md.md)]では、一部の型情報をコンパイル時に静的に推論できず、代わりに実行時に動的に取得する場合、そのような型情報やコードを維持または生成しないことがあります。  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]は、リフレクションと動的プログラミングを有効にします。 ただし、すべての型をリフレクション対象としてマークできるわけではありません。そうすると、生成されるコード サイズが大きくなりすぎるため \(特に、.NET Framework での パブリック API へのリフレクションがサポートされているため\) です。[!INCLUDE[net_native](../../../includes/net-native-md.md)] コンパイラは、どの型でリフレクションをサポートする必要があるかを適切に判断し、それらの型についてのみメタデータを維持し、コードを生成します。  
  
 たとえば、データ バインディングは、プロパティ名を関数にマップするためにアプリを必要とします。 Windows ストア アプリ用 .NET では、共通言語ランタイムが自動的にリフレクションを使用して、マネージド型および公開されているネイティブ型にこの機能を提供します。[!INCLUDE[net_native](../../../includes/net-native-md.md)]では、データのバインド先の型のメタデータが、コンパイラによって自動的に含められます。  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] コンパイラは、ヒントやディレクティブなしで機能する、<xref:System.Collections.Generic.List%601> や <xref:System.Collections.Generic.Dictionary%602> などの一般的に使用されるジェネリック型も処理できます。[dynamic](../Topic/dynamic%20\(C%23%20Reference\).md) キーワードも、一定の制限の下でサポートされます。  
  
> [!NOTE]
>  アプリを [!INCLUDE[net_native](../../../includes/net-native-md.md)]に移植するときには、すべての動的コード パスを十分にテストする必要があります。  
  
 ほとんどの開発者にとっては [!INCLUDE[net_native](../../../includes/net-native-md.md)]の既定の構成で十分ですが、開発者によっては、ランタイム ディレクティブ \(.rd.xml\) ファイルを使用した構成の微調整が必要となる場合もあります。 さらに、場合によっては、[!INCLUDE[net_native](../../../includes/net-native-md.md)] コンパイラがリフレクションで使用できるようにする必要があるメタデータを判断できず、ヒントを利用することがあります。特に次のような場合です。  
  
-   <xref:System.Type.MakeGenericType%2A?displayProperty=fullName> や <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=fullName> などの一部の構造体は、静的に決定できません。  
  
-   コンパイラでインスタンス化を決定できないため、リフレクション対象のジェネリック型をランタイム ディレクティブで指定する必要があります。 これは、すべてのコードを含める必要があるだけではなく、ジェネリック型へのリフレクションによって無限サイクルが生じる可能性があるためです \(たとえば、ジェネリック型でジェネリック メソッドが呼び出された場合\)。  
  
> [!NOTE]
>  ランタイム ディレクティブは、ランタイム ディレクティブ \(.rd.xml\) ファイルで定義されます。 このファイルの使用に関する全般的な情報については、「[作業の開始](../../../docs/framework/net-native/getting-started-with-net-native.md)」をご覧ください。 ランタイム ディレクティブについては、「[ランタイム ディレクティブ \(rd.xml\) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)」をご覧ください。  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]には、既定セット以外のどの型でリフレクションをサポートするかを開発者が決定するときに役立つプロファイリング ツールも含まれています。  
  
<a name="Reflection"></a>   
## リフレクションに関するその他の違い  
 Windows ストア アプリ用 .NET と [!INCLUDE[net_native](../../../includes/net-native-md.md)]の間には、その動作にリフレクション関連のその他の個別の違いが多数あります。  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] の場合:  
  
-   .NET Framework クラス ライブラリでの型とメンバーに対するプライベート リフレクションはサポートされません。 ただし、独自のプライベート型とメンバー、およびサードパーティ ライブラリの型とメンバーに対するリフレクションは行うことができます。  
  
-   <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=fullName> プロパティは、戻り値を表す `false` オブジェクトに対し、正しく <xref:System.Reflection.ParameterInfo> を返します。 Windows ストア アプリ用 .NET の場合、これは `true` を返します。 中間言語 \(IL\) はこれを直接サポートせず、解釈は言語に任されます。  
  
-   <xref:System.RuntimeFieldHandle> 構造体と <xref:System.RuntimeMethodHandle> 構造体のパブリック メンバーはサポートされません。 これらの型は、LINQ、式ツリー、および静的な配列の初期化でのみサポートされます。  
  
-   <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=fullName> と <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=fullName> の基底クラスには隠ぺいされたメンバーが含まれるため、明示的なオーバーライドなしでオーバーライドできます。 これは、その他の [RuntimeReflectionExtensions.GetRuntime\*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) メソッドの場合も同様です。  
  
-   <xref:System.Type.MakeArrayType%2A?displayProperty=fullName> と <xref:System.Type.MakeByRefType%2A?displayProperty=fullName> は、特定の組み合わせ \(たとえば、byref の配列\) を作成しようとしたときに失敗しません。  
  
-   リフレクションを使用して、ポインター パラメーターを持つメンバーを呼び出すことはできません。  
  
-   リフレクションを使用して、ポインター フィールドを取得または設定することはできません。  
  
-   引数カウントが間違っていて、いずれかの引数の型が正しくない場合、[!INCLUDE[net_native](../../../includes/net-native-md.md)]は <xref:System.ArgumentException> ではなく <xref:System.Reflection.TargetParameterCountException> をスローします。  
  
-   通常、例外のバイナリ シリアル化はサポートされません。 そのため、シリアル化不可能なオブジェクトを <xref:System.Exception.Data%2A?displayProperty=fullName> ディクショナリに追加できます。  
  
<a name="Unsupported"></a>   
## サポートされていないシナリオと API  
 次のセクションに、全般的な開発、相互運用、および HTTPClient や Windows Communication Foundation \(WCF\) などの技術でサポートされないシナリオと API を示します。  
  
-   [全般的な開発](#General)  
  
-   [HttpClient](#HttpClient)  
  
-   [Interop](#Interop)  
  
-   [サポートされていない API](#APIs)  
  
<a name="General"></a>   
### 全般的な開発の違い  
 **値型**  
  
-   値型の <xref:System.ValueType.Equals%2A?displayProperty=fullName> メソッドと <xref:System.ValueType.GetHashCode%2A?displayProperty=fullName> メソッドをオーバーライドする場合は、基底クラスの実装を呼び出さないでください。 Windows ストア アプリ用 .NET では、これらのメソッドはリフレクションに依存します。 コンパイル時に、[!INCLUDE[net_native](../../../includes/net-native-md.md)]はランタイム リフレクションに依存しない実装を生成します。 つまり、これら 2 つのメソッドをオーバーライドしなければ、[!INCLUDE[net_native](../../../includes/net-native-md.md)]によってコンパイル時に実装が生成されるため、これらのメソッドは期待どおりに動作します。 ただし、基底クラスの実装を呼び出さずにこれらのメソッドをオーバーライドすると、例外が発生します。  
  
-   1 メガバイトより大きい値型はサポートされません。  
  
-   値型は、[!INCLUDE[net_native](../../../includes/net-native-md.md)]で既定のコンストラクターを持つことができません。 \(C\# と Visual Basic では、値型の既定のコンストラクターが許可されません。 ただし、IL ではこれらを作成できます。\)  
  
 **配列**  
  
-   ゼロ以外の下限を持つ配列はサポートされません。 通常、これらの配列は [Array.CreateInstance\(Type, Int32\[\], Int32\<xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=fullName> オーバーロードを呼び出すことで作成されます。  
  
-   多次元配列の動的作成はサポートされません。 そのような配列は通常、<xref:System.Array.CreateInstance%2A?displayProperty=fullName> パラメーターを含む `lengths` メソッドのオーバーロードを呼び出すか、<xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=fullName> メソッドを呼び出すことで作成されます。  
  
-   4 つ以上の次元を持つ多次元配列 \(つまり、<xref:System.Array.Rank%2A?displayProperty=fullName> プロパティ値が 4 以上のもの\) はサポートされません。 代わりに[ジャグ配列](../Topic/Jagged%20Arrays%20\(C%23%20Programming%20Guide\).md) \(配列の配列\) を使用してください。 たとえば、`array[x,y,z]` は無効ですが、`array[x][y][z]` は有効です。  
  
-   多次元配列の共変性はサポートされず、実行時に <xref:System.InvalidCastException> 例外を発生させます。  
  
 **ジェネリック**  
  
-   ジェネリック型の無限展開はコンパイル エラーになります。 たとえば、このコードはコンパイルに失敗します。  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 **ポインター**  
  
-   ポインターの配列はサポートされていません。  
  
-   リフレクションを使用して、ポインター フィールドを取得または設定することはできません。  
  
 **シリアル化**  
  
 <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> 属性はサポートされていません。 代わりに <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> 属性を使用してください。  
  
 **リソース**  
  
 <xref:System.Diagnostics.Tracing.EventSource> クラスでのローカライズされたリソースの使用はサポートされません。<xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=fullName> プロパティはローカライズされたリソースを定義しません。  
  
 **デリゲート**  
  
 `Delegate.BeginInvoke` と `Delegate.EndInvoke` はサポートされません。  
  
 **Async**  
  
 Task IAsync のオーバーロードでのスレッドのロジックはサポートされません。  
  
 **その他の API**  
  
-   <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=fullName> 属性が型に適用されない場合、<xref:System.PlatformNotSupportedException> プロパティは <xref:System.Runtime.InteropServices.GuidAttribute> 例外をスローします。 GUID は主に COM サポートで使用されます。  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=fullName> メソッドは、[!INCLUDE[net_native](../../../includes/net-native-md.md)]で、短い日付を含む文字列を正しく解析します。 ただし、Microsoft サポート技術情報の記事 [KB2803771](http://support.microsoft.com/kb/2803771) と [KB2803755](http://support.microsoft.com/kb/2803755) で説明されている日付と時刻の解析の変更に対する互換性は保持されません。  
  
-   <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=fullName> `("E")` は [!INCLUDE[net_native](../../../includes/net-native-md.md)]で正しく丸められます。 CLR の一部のバージョンでは、結果の文字列が丸められるのではなく、切り捨てられます。  
  
<a name="HttpClient"></a>   
### HttpClient の違い  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] では、<xref:System.Net.Http.HttpClientHandler> クラスは、標準の Windows ストア アプリ用 .NET で使用される <xref:System.Net.WebRequest> クラスと <xref:System.Net.WebResponse> クラスの代わりに、WinINet を \([HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) クラスを通じて\) 内部で使用します。  WinINet では、<xref:System.Net.Http.HttpClientHandler> クラスでサポートされる構成オプションがすべてサポートされるわけではありません。  結果は次のようになります。  
  
-   <xref:System.Net.Http.HttpClientHandler> の機能プロパティの一部は `false`では [!INCLUDE[net_native](../../../includes/net-native-md.md)] を返しますが、標準の Windows ストア アプリ用 .NET では `true` を返します。  
  
-   構成プロパティ `get` アクセサーの一部は、[!INCLUDE[net_native](../../../includes/net-native-md.md)]で、常に、Windows ストア アプリ用 .NET の既定の構成値とは異なる固定値を返します。  
  
 次のサブセクションで、その他の動作の違いについて説明します。  
  
 **プロキシ**  
  
 [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) クラスは、要求ごとのプロキシの構成とオーバーライドをサポートしません。  つまり、[!INCLUDE[net_native](../../../includes/net-native-md.md)]では、すべての要求が、<xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=fullName> プロパティの値に応じて、システム構成のプロキシ サーバーを使用するか、プロキシ サーバーを使用しません。  Windows ストア アプリ用 .NET では、プロキシ サーバーは <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=fullName> プロパティにより定義されます。[!INCLUDE[net_native](../../../includes/net-native-md.md)]では、<xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=fullName> を `null` 以外の値に設定すると、<xref:System.PlatformNotSupportedException> 例外がスローされます。<xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=fullName> プロパティは、`false`では [!INCLUDE[net_native](../../../includes/net-native-md.md)] を返しますが、標準の Windows ストア アプリ用 .NET Framework では `true` を返します。  
  
 **自動リダイレクト**  
  
 [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) クラスでは、自動リダイレクトの最大数の構成が許可されません。  標準の Windows ストア アプリ用 .NET での <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=fullName> プロパティの値は既定で 50 で、変更できません。[!INCLUDE[net_native](../../../includes/net-native-md.md)]では、このプロパティの値は 10 で、変更しようとすると <xref:System.PlatformNotSupportedException> 例外がスローされます。<xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=fullName> プロパティは `false`では [!INCLUDE[net_native](../../../includes/net-native-md.md)] を返し、Windows ストア アプリ用 .NET では `true` を返します。  
  
 **自動展開**  
  
 Windows ストア アプリ用 .NET では、<xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=fullName> プロパティを <xref:System.Net.DecompressionMethods>、<xref:System.Net.DecompressionMethods>、<xref:System.Net.DecompressionMethods> と <xref:System.Net.DecompressionMethods> の両方、または <xref:System.Net.DecompressionMethods> に設定できます。[!INCLUDE[net_native](../../../includes/net-native-md.md)]では、<xref:System.Net.DecompressionMethods> と <xref:System.Net.DecompressionMethods> を共に設定するか、<xref:System.Net.DecompressionMethods> の設定のみがサポートされます。<xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> プロパティを <xref:System.Net.DecompressionMethods> のみまたは <xref:System.Net.DecompressionMethods> のみに設定しようとすると、<xref:System.Net.DecompressionMethods> と <xref:System.Net.DecompressionMethods> の両方に自動的に設定されます。  
  
 **クッキー**  
  
 クッキーの処理は、<xref:System.Net.Http.HttpClient> と WinINet により同時に行われます。<xref:System.Net.CookieContainer> のクッキーは、WinINet クッキー キャッシュのクッキーと組み合わされます。<xref:System.Net.CookieContainer> のクッキーを削除すると <xref:System.Net.Http.HttpClient> からクッキーが送信されませんが、クッキーが既に WinINet に示されており、ユーザーによって削除されない場合、WinINet がクッキーを送信します。<xref:System.Net.Http.HttpClient>、<xref:System.Net.Http.HttpClientHandler>、または <xref:System.Net.CookieContainer> API を使用して、プログラムにより WinINet からクッキーを削除することはできません。<xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=fullName> プロパティを `false` に設定しても、<xref:System.Net.Http.HttpClient> からクッキーが送信されなくなるのみで、WinINet の要求にはまだそのクッキーが含まれている可能性があります。  
  
 **資格情報**  
  
 Windows ストア アプリ用 .NET では、<xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=fullName> プロパティと <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=fullName> プロパティは独立して動作します。  また、<xref:System.Net.Http.HttpClientHandler.Credentials%2A> プロパティは <xref:System.Net.ICredentials> インターフェイスを実装するオブジェクトをすべて受け入れます。[!INCLUDE[net_native](../../../includes/net-native-md.md)]では、<xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> プロパティを `true` に設定すると、<xref:System.Net.Http.HttpClientHandler.Credentials%2A> プロパティが `null` になります。  さらに、<xref:System.Net.Http.HttpClientHandler.Credentials%2A> プロパティは、`null`、<xref:System.Net.CredentialCache.DefaultCredentials%2A>、または <xref:System.Net.NetworkCredential> 型のオブジェクトにしか設定できません。  その他の <xref:System.Net.ICredentials> オブジェクト \(最も一般的なものは <xref:System.Net.CredentialCache>\) を <xref:System.Net.Http.HttpClientHandler.Credentials%2A> プロパティに割り当てると、<xref:System.PlatformNotSupportedException> がスローされます。  
  
 **その他のサポートされていない機能または構成できない機能**  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] の場合:  
  
-   <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=fullName> プロパティの値は常に <xref:System.Net.Http.ClientCertificateOption> です。  Windows ストア アプリ用 .NET での既定値は <xref:System.Net.Http.ClientCertificateOption> です。  
  
-   <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=fullName> プロパティは構成できません。  
  
-   <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=fullName> プロパティは常に `true` です。  Windows ストア アプリ用 .NET での既定値は `false` です。  
  
-   応答の `SetCookie2` ヘッダーは廃止されたものとして無視されます。  
  
<a name="Interop"></a>   
### 相互運用の違い  
 **非推奨 API**  
  
 マネージド コードで相互運用性のために使用される頻度が低い API のいくつかが、非推奨になっています。 これらの API を [!INCLUDE[net_native](../../../includes/net-native-md.md)]で使用すると、<xref:System.NotImplementedException> 例外か <xref:System.PlatformNotSupportedException> 例外がスローされるか、コンパイラ エラーになる場合があります。 Windows ストア アプリ用 .NET では、これらの API は廃止としてマークされていますが、これらの API を呼び出すとコンパイラ エラーではなくコンパイラの警告が生成されます。  
  
 非推奨の `VARIANT` マーシャリング用 API:  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.VarEnum?displayProperty=fullName>|  
  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> はサポートされていますが、[IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) や byref バリアントと共に使用された場合など、一部のシナリオでは例外がスローされます。  
  
 非推奨の [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) サポート用 API:  
  
|型|メンバー|  
|-------|----------|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.ClassInterfaceType>|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.ClassInterfaceType>|  
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=fullName>|属性はサポートされません。|  
  
 非推奨のクラシック COM イベント用 API:  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=fullName>|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|  
  
 非推奨の <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=fullName> インターフェイスの API \([!INCLUDE[net_native](../../../includes/net-native-md.md)]では非サポート\):  
  
|種類|メンバー|  
|--------|----------|  
|<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=fullName>|すべてのメンバー。|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=fullName>|すべてのメンバー。|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=fullName>|すべてのメンバー。|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>|  
  
 その他のサポートされない相互運用機能:  
  
|種類|メンバー|  
|--------|----------|  
|<xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=fullName>|すべてのメンバー。|  
|<xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=fullName>|すべてのメンバー。|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>|<xref:System.Runtime.InteropServices.UnmanagedType>|  
  
 ほとんど使用されないマーシャリング API:  
  
|種類|メンバー|  
|--------|----------|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=fullName>|<xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29>|  
  
 **プラットフォーム呼び出しと COM 相互運用の互換性**  
  
 ほとんどのプラットフォーム呼び出しと COM 相互運用シナリオは、[!INCLUDE[net_native](../../../includes/net-native-md.md)]でもサポートされます。 特に、Windows ランタイム \(WinRT\) API とのすべての相互運用性と Windows ランタイムで必要なすべてのマーシャリングがサポートされます。 これには、次のものに対するマーシャリング サポートが含まれます。  
  
-   配列 \(<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> を含む\)  
  
-   `BStr`  
  
-   デリゲート  
  
-   文字列 \(Unicode、Ansi、および HSTRING\)  
  
-   構造体 \(`byref` と `byval`\)  
  
-   Unions  
  
-   Win32 ハンドル  
  
-   すべての WinRT 構造体  
  
-   マーシャリング バリアント型の部分的なサポート。 次の型がサポートされます。  
  
    -   <xref:System.Boolean>  
  
    -   <xref:System.Byte>  
  
    -   <xref:System.Decimal>  
  
    -   <xref:System.Double>  
  
    -   <xref:System.Int16>  
  
    -   <xref:System.Int32>  
  
    -   <xref:System.Int64>  
  
    -   <xref:System.SByte>  
  
    -   <xref:System.Single>  
  
    -   <xref:System.UInt16>  
  
    -   <xref:System.UInt32>  
  
    -   <xref:System.UInt64>  
  
    -   `BStr`  
  
    -   [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509.aspx)  
  
 ただし、[!INCLUDE[net_native](../../../includes/net-native-md.md)]では、次のことはサポートされません。  
  
-   クラシック COM イベントの使用  
  
-   マネージド型での <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=fullName> インターフェイスの実装  
  
-   <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=fullName> 属性を使用したマネージ型での [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) インターフェイスの実装。 ただし、`IDispatch` から COM オブジェクトを呼び出すことはできず、マネージド オブジェクトは `IDispatch` を実装できないことに注意してください。  
  
 リフレクションを使用したプラットフォーム呼び出しメソッドの呼び出しはサポートされません。 この制限を回避するには、別のメソッドでメソッド呼び出しをラップし、リフレクションを使用してラッパーを代わりに呼び出します。  
  
<a name="APIs"></a>   
### その他の Windows ストア アプリ用 .NET API との違い  
 このセクションには、[!INCLUDE[net_native](../../../includes/net-native-md.md)]でサポートされないその他の API を示します。 サポートされない API で最も多いのは、Windows Communication Foundation \(WCF\) API です。  
  
 **DataAnnotations \(System.ComponentModel.DataAnnotations\)**  
  
 <xref:System.ComponentModel.DataAnnotations> 名前空間と <xref:System.ComponentModel.DataAnnotations.Schema> 名前空間内の型は、[!INCLUDE[net_native](../../../includes/net-native-md.md)]ではサポートされません。 これらには、Windows 8 の Windows ストア アプリ用 .NET に存在する次の型が含まれます。  
  
||  
|-|  
|<xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EditableAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=fullName>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=fullName>|  
  
 **Visual Basic**  
  
 Visual Basic は、現在 [!INCLUDE[net_native](../../../includes/net-native-md.md)]ではサポートされていません。<xref:Microsoft.VisualBasic> 名前空間と <xref:Microsoft.VisualBasic.CompilerServices> 名前空間内の次の型は、[!INCLUDE[net_native](../../../includes/net-native-md.md)]では使用できません。  
  
||  
|-|  
|<xref:Microsoft.VisualBasic.CallType?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.Constants?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.Strings?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=fullName>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=fullName>|  
  
 **リフレクション コンテキスト \(System.Reflection.Context 名前空間\)**  
  
 <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=fullName> クラスは [!INCLUDE[net_native](../../../includes/net-native-md.md)]ではサポートされません。  
  
 **RTC \(System.Net.Http.Rtc\)**  
  
 <xref:System.Net.Http.RtcRequestFactory?displayProperty=fullName> クラスは [!INCLUDE[net_native](../../../includes/net-native-md.md)]ではサポートされません。  
  
 **Windows Communication Foundation \(WCF\) \(System.ServiceModel.\*\)**  
  
 [System.ServiceModel.\* 名前空間](http://msdn.microsoft.com/library/gg145010.aspx) 内の型は、[!INCLUDE[net_native](../../../includes/net-native-md.md)] ではサポートされません。 そうした型には、次のようなものがあります。  
  
||  
|-|  
|<xref:System.ServiceModel.ActionNotSupportedException?displayProperty=fullName>|  
|<xref:System.ServiceModel.BasicHttpBinding?displayProperty=fullName>|  
|<xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=fullName>|  
|<xref:System.ServiceModel.BasicHttpSecurity?displayProperty=fullName>|  
|<xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=fullName>|  
|<xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.ChannelFactory?displayProperty=fullName>|  
|<xref:System.ServiceModel.ChannelFactory%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=fullName>|  
|<xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=fullName>|  
|<xref:System.ServiceModel.CommunicationException?displayProperty=fullName>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=fullName>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=fullName>|  
|<xref:System.ServiceModel.CommunicationState?displayProperty=fullName>|  
|<xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=fullName>|  
|<xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.DuplexClientBase%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.EndpointAddress?displayProperty=fullName>|  
|<xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=fullName>|  
|<xref:System.ServiceModel.EndpointIdentity?displayProperty=fullName>|  
|<xref:System.ServiceModel.EndpointNotFoundException?displayProperty=fullName>|  
|<xref:System.ServiceModel.EnvelopeVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.ExceptionDetail?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultCode?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultContractAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultException?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultException%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultReason?displayProperty=fullName>|  
|<xref:System.ServiceModel.FaultReasonText?displayProperty=fullName>|  
|<xref:System.ServiceModel.HttpBindingBase?displayProperty=fullName>|  
|<xref:System.ServiceModel.HttpClientCredentialType?displayProperty=fullName>|  
|<xref:System.ServiceModel.HttpTransportSecurity?displayProperty=fullName>|  
|<xref:System.ServiceModel.IClientChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.ICommunicationObject?displayProperty=fullName>|  
|<xref:System.ServiceModel.IContextChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=fullName>|  
|<xref:System.ServiceModel.IExtensibleObject%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.IExtension%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.IExtensionCollection%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.InstanceContext?displayProperty=fullName>|  
|<xref:System.ServiceModel.InvalidMessageContractException?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageContractAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageCredentialType?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageHeader%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageHeaderException?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=fullName>|  
|<xref:System.ServiceModel.MessageSecurityVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.NetHttpBinding?displayProperty=fullName>|  
|<xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=fullName>|  
|<xref:System.ServiceModel.NetTcpBinding?displayProperty=fullName>|  
|<xref:System.ServiceModel.NetTcpSecurity?displayProperty=fullName>|  
|<xref:System.ServiceModel.OperationContext?displayProperty=fullName>|  
|<xref:System.ServiceModel.OperationContextScope?displayProperty=fullName>|  
|<xref:System.ServiceModel.OperationContractAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.OperationFormatStyle?displayProperty=fullName>|  
|<xref:System.ServiceModel.ProtocolException?displayProperty=fullName>|  
|<xref:System.ServiceModel.QuotaExceededException?displayProperty=fullName>|  
|<xref:System.ServiceModel.SecurityMode?displayProperty=fullName>|  
|<xref:System.ServiceModel.ServerTooBusyException?displayProperty=fullName>|  
|<xref:System.ServiceModel.ServiceActivationException?displayProperty=fullName>|  
|<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=fullName>|  
|<xref:System.ServiceModel.TcpClientCredentialType?displayProperty=fullName>|  
|<xref:System.ServiceModel.TcpTransportSecurity?displayProperty=fullName>|  
|<xref:System.ServiceModel.TransferMode?displayProperty=fullName>|  
|<xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=fullName>|  
|<xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=fullName>|  
|<xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.AddressHeader?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.FaultConverter?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IInputChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IInputSession?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IOutputSession?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ISession?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.Message?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageFault?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageHeader?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageProperties?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageState?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.MessageVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.RequestContext?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=fullName>|  
|<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.ClientCredentials?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.ContractDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.FaultDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageDirection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.OperationDescription?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=fullName>|  
|<xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=fullName>|  
|<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.SecurityVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.TrustVersion?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=fullName>|  
|<xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=fullName>|  
  
### シリアライザーの違い  
 <xref:System.Runtime.Serialization.DataContractSerializer>、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>、および <xref:System.Xml.Serialization.XmlSerializer> クラスによるシリアル化と逆シリアル化に関する違いを次に示します。  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)]では、<xref:System.Runtime.Serialization.DataContractSerializer> と <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、型がルート シリアル化型ではない基底クラス メンバーを持つ派生クラスのシリアル化または逆シリアル化に失敗します。 たとえば、次のコードでは、`Y` をシリアル化または逆シリアル化しようとするとエラーになります。  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     基底クラスのメンバーはシリアル化時にスキャンされないため、`InnerType` 型はシリアライザーに認識されていません。  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> と <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、<xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装するクラスまたは構造体のシリアル化に失敗します。 たとえば、次の型ではシリアル化と逆シリアル化が失敗します。  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> は、シリアル化するオブジェクトの正確な型を認識していないため、次のオブジェクト値をシリアル化できません。  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> は、シリアル化されるオブジェクトの型が <xref:System.Xml.XmlQualifiedName> の場合、シリアル化と逆シリアル化に失敗します。  
  
-   すべてのシリアライザー \(<xref:System.Runtime.Serialization.DataContractSerializer>、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>、および <xref:System.Xml.Serialization.XmlSerializer>\) は、<xref:System.Xml.Linq.XElement?displayProperty=fullName> 型または <xref:System.Xml.Linq.XElement> を含む型のシリアル化コードを生成できません。 代わりに、ビルド時エラーが表示されます。  
  
-   次のシリアル化型のコンストラクターが、期待どおりに動作する保証はありません。  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=fullName>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=fullName>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=fullName>  
  
    -   [XmlSerializer.XmlSerializer\(Type, Type\<xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=fullName>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=fullName>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=fullName>  
  
    -   [XmlSerializer.XmlSerializer\(Type, XmlAttributeOverrides, Type\<xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=fullName>  
  
-   <xref:System.Xml.Serialization.XmlSerializer> は、次のいずれかの属性が設定されているメソッドを持つ型のコードを生成できません。  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Xml.Serialization.XmlSerializer> は、<xref:System.Xml.Serialization.IXmlSerializable> カスタム シリアル化インターフェイスを受け入れません。 このインターフェイスを実装するクラスがある場合、<xref:System.Xml.Serialization.XmlSerializer> は型を Plain Old CLR Object \(POCO\) 型であると見なし、そのパブリック プロパティのみをシリアル化します。  
  
-   次のようなプレーンな <xref:System.Exception> オブジェクトのシリアル化は、<xref:System.Runtime.Serialization.DataContractSerializer> と <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> では正しく行われません。  
  
  
  
<a name="VS"></a>   
## Visual Studio の違い  
 **例外とデバッグ**  
  
 デバッガーで [!INCLUDE[net_native](../../../includes/net-native-md.md)]を使用してコンパイルされたアプリを実行する場合、次の例外の種類について初回例外が有効になります。  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 **アプリのビルド**  
  
 Visual Studio で既定で使用される x86 ビルド ツールを使用します。 C:\\Program Files \(x86\)\\MSBuild\\12.0\\bin\\amd64 にある AMD64 MSBuild ツールは、ビルドの問題が発生する可能性があるため、使用しないことをお勧めします。  
  
 **プロファイラー**  
  
-   Visual Studio CPU プロファイラーと XAML メモリ プロファイラーでは、マイ コードのみは正しく表示されません。  
  
-   XAML メモリ プロファイラーでは、マネージド ヒープ データが正しく表示されません。  
  
-   CPU プロファイラーでは、モジュールが正しく識別されず、プレフィックス付きの関数名が表示されます。  
  
 **単体テスト ライブラリ プロジェクト**  
  
 Windows ストア アプリ用単体テスト ライブラリ プロジェクトで [!INCLUDE[net_native](../../../includes/net-native-md.md)]を有効にすることはサポートされていません。有効にすると、プロジェクトはビルドに失敗します。  
  
## 参照  
 [作業の開始](../../../docs/framework/net-native/getting-started-with-net-native.md)   
 [ランタイム ディレクティブ \(rd.xml\) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Windows ストア アプリ用 .NET の概要](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)   
 [Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)