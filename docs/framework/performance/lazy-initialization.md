---
title: "限定的な初期化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "限定的な初期化 (.NET での), 概要"
ms.assetid: 56b4ae5c-4745-44ff-ad78-ffe4fcde6b9b
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 20
---
# 限定的な初期化
オブジェクトの*限定的な初期化*とは、初めて使用されるときまでオブジェクトの作成を延期することです \(このトピックでは、"*限定的な初期化*" と "*限定的なインスタンス化*" という用語を同じ意味で使用しています\)。限定的な初期化は主に、パフォーマンスの向上、無駄な計算の回避、およびプログラムのメモリ要件の軽減を目的として使用されます。  最も一般的なシナリオは次のとおりです。  
  
-   オブジェクトの作成時の負荷が高く、プログラムではそれを使用しない可能性がある場合。  たとえば、メモリにある `Customer` オブジェクトの `Orders` プロパティに `Order` オブジェクトの大きな配列が格納されていて、このオブジェクトを初期化するにはデータベースに接続する必要があるとします。  Orders のデータを表示したり計算で使用したりすることをユーザーから要求されない限り、そのオブジェクトを作成するためにシステム メモリや計算サイクルを使用する必要はありません。  `Orders` オブジェクトの宣言で `Lazy<Orders>` を使用して限定的な初期化を指定すると、オブジェクトが使用されていないときのシステム リソースの浪費を回避できます。  
  
-   オブジェクトの作成時の負荷が高く、負荷が高い他の操作が完了するまでそのオブジェクトの作成を延期する場合。  たとえば、プログラムの起動時にいくつかのオブジェクト インスタンスが読み込まれても、すぐに必要なものはそのうちの一部だけであるとします。  この場合、必要なオブジェクトが作成されるまで不要なオブジェクトの初期化を延期すると、プログラムの起動時のパフォーマンスを向上させることができます。  
  
 限定的な初期化を実行するためのコードは独自に記述することもできますが、代わりに <xref:System.Lazy%601> を使用することをお勧めします。  <xref:System.Lazy%601> とその関連型はスレッド セーフもサポートしており、例外の反映ポリシーにも一貫性があります。  
  
 限定的な初期化をさまざまなシナリオで有効にするために用意されている .NET Framework Version 4 の型の一覧を次に示します。  
  
|型|説明|  
|-------|--------|  
|<xref:System.Lazy%601>|任意のクラス ライブラリまたはユーザー定義の型に限定的な初期化のセマンティクスを提供するラッパー クラスです。|  
|<xref:System.Threading.ThreadLocal%601>|<xref:System.Lazy%601> に似ていますが、スレッド ローカルに基づく限定的な初期化のセマンティクスを提供します。  各スレッドは、独自の一意の値にアクセスできます。|  
|<xref:System.Threading.LazyInitializer>|クラスのオーバーヘッドがないオブジェクトの限定的な初期化のために、高度な `static` \(Visual Basic では `Shared`\) メソッドを提供します。|  
  
## 基本の限定的な初期化  
 たとえば `MyType` という限定的に初期化された型を定義するには、次の例に示すように、`Lazy<MyType>` \(Visual Basic では `Lazy(Of MyType)`\) を使用します。  <xref:System.Lazy%601> コンストラクターにデリゲートが渡されていない場合、値プロパティに最初にアクセスしたときに、ラップされた型が <xref:System.Activator.CreateInstance%2A?displayProperty=fullName> を使用して作成されます。  型に既定のコンストラクターがない場合は、実行時例外がスローされます。  
  
 次の例では、`Orders` というクラスに、データベースから取得される `Order` オブジェクトの配列が含まれているものとします。  `Customer` オブジェクトに `Orders` のインスタンスが含まれていますが、ユーザーの操作によっては、`Orders` オブジェクトのデータが不要な場合があります。  
  
 [!code-csharp[Lazy#1](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#1)]
 [!code-vb[Lazy#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#1)]  
  
 次の例に示すように、ラップされた型に対する特定のコンストラクター オーバーロードを作成時に呼び出す <xref:System.Lazy%601> コンストラクターにデリゲートを渡して、必要な他の初期化の手順を実行することもできます。  
  
 [!code-csharp[Lazy#2](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#2)]
 [!code-vb[Lazy#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#2)]  
  
 限定的なオブジェクトの作成後、限定的な変数の <xref:System.Lazy%601.Value%2A> プロパティに初めてアクセスするまでは、`Orders` は作成されません。  最初のアクセス時に、ラップされた型が作成されて返され、後でアクセスできるように保存されます。  
  
 [!code-csharp[Lazy#3](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#3)]
 [!code-vb[Lazy#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#3)]  
  
 <xref:System.Lazy%601> オブジェクトは、初期化の際に使用されたものと同じオブジェクトまたは値を常に返します。  したがって、<xref:System.Lazy%601.Value%2A> プロパティは読み取り専用です。  <xref:System.Lazy%601.Value%2A> に参照型が格納されている場合、それに新しいオブジェクトを割り当てることはできません \(ただし、設定可能なパブリック フィールドとプロパティの値は変更できます\)。<xref:System.Lazy%601.Value%2A> に値型が格納されている場合、その値を変更することはできません。  ただし、新しい引数を使用して変数のコンストラクターをもう一度呼び出すと、新しい変数を作成できます。  
  
 [!code-csharp[Lazy#4](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#4)]
 [!code-vb[Lazy#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#4)]  
  
 前の例と同様に、この新しい限定的なインスタンスでは、<xref:System.Lazy%601.Value%2A> プロパティに初めてアクセスするまで `Orders` がインスタンス化されません。  
  
### スレッド セーフな初期化  
 既定では、<xref:System.Lazy%601> オブジェクトはスレッド セーフです。  つまり、コンストラクターでスレッド セーフの種類を指定しない場合、作成される <xref:System.Lazy%601> オブジェクトはスレッド セーフです。  マルチスレッドのシナリオでは、スレッド セーフな <xref:System.Lazy%601> オブジェクトの <xref:System.Lazy%601.Value%2A> プロパティに最初にアクセスしたスレッドが初期化を行います。その後はどのスレッドからもそのデータにアクセスするため、すべてのスレッドで同じデータが共有されます。  したがって、どのスレッドがオブジェクトを初期化したかは問題にならず、競合状態が発生しません。  
  
> [!NOTE]
>  例外のキャッシュを使用する場合、この一貫性はエラー状態にも当てはまります。  詳細については、次のセクション" [遅延オブジェクトの例外](../../../docs/framework/performance/lazy-initialization.md#ExceptionsInLazyObjects)参照します。  
  
 3 つの異なるスレッドで、同じ値を持つ同じ `Lazy<int>` インスタンスを使用している例を次に示します。  
  
 [!code-csharp[Lazy#8](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#8)]
 [!code-vb[Lazy#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#8)]  
  
 スレッドごとに異なるデータが必要な場合は、この後で説明するように <xref:System.Threading.ThreadLocal%601> 型を使用します。  
  
 一部の <xref:System.Lazy%601> コンストラクターには、`isThreadSafe` という名前のブール値パラメーターがあります。これは、<xref:System.Lazy%601.Value%2A> プロパティに複数のスレッドからアクセスするかどうかを指定するために使用します。  プロパティに 1 つのスレッドからのみアクセスする場合は、少しでもパフォーマンスが向上するように `false` を渡します。  プロパティに複数のスレッドからアクセスする場合は、`true` を渡して、初期化時にいずれかのスレッドから例外がスローされたときに競合状態を正しく処理できるように <xref:System.Lazy%601> インスタンスに指示します。  
  
 一部の <xref:System.Lazy%601> コンストラクターには、`mode` という名前の <xref:System.Threading.LazyThreadSafetyMode> パラメーターがあります。  これらのコンストラクターでは、追加のスレッド セーフ モードが提供されます。  <xref:System.Lazy%601> オブジェクトのスレッド セーフが、スレッド セーフを指定するコンストラクター パラメーターによって受ける影響を次の表に示します。  各コンストラクターには、このようなパラメーターが 1 つのみあります。  
  
|オブジェクトのスレッド セーフ|`LazyThreadSafetyMode` `mode` パラメーター|`isThreadSafe` ブール値パラメーター|スレッド セーフ パラメーターなし|  
|---------------------|------------------------------------------|-------------------------------|-----------------------|  
|完全なスレッドセーフ。値の初期化を試行するスレッドは一度に 1 つのみです。|<xref:System.Threading.LazyThreadSafetyMode>|`true`|はい。|  
|スレッド セーフではない。|<xref:System.Threading.LazyThreadSafetyMode>|`false`|使用できません。|  
|完全なスレッドセーフ。値を初期化するためにスレッドが競合します。|<xref:System.Threading.LazyThreadSafetyMode>|使用できません。|使用できません。|  
  
 表に示されているように、`mode` パラメーターに <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> を指定することは、`isThreadSafe` パラメーターに `true` を指定することと同じです。また、<xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> を指定することは、`false` を指定することと同じです。  
  
 <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> を指定すると、複数のスレッドで <xref:System.Lazy%601> インスタンスの初期化を試行します。  実際に初期化を実行できるスレッドは 1 つだけで、その他のすべてのスレッドは初期化に成功したスレッドによって初期化された値を受け取ります。  初期化時にスレッドで例外がスローされた場合、そのスレッドは成功したスレッドによって設定された値を受け取りません。  例外はキャッシュされないため、後で <xref:System.Lazy%601.Value%2A> プロパティにアクセスしようとした場合、初期化に成功することがあります。  これは、他のモードでの例外処理方法とは異なります。その点については、次のセクションで説明します。  詳細については、<xref:System.Threading.LazyThreadSafetyMode> 列挙体の解説を参照してください。  
  
<a name="ExceptionsInLazyObjects"></a>   
## 遅延オブジェクトの例外  
 既に説明したとおり、<xref:System.Lazy%601> オブジェクトは、初期化の際に使用されたものと同じオブジェクトまたは値を常に返すため、<xref:System.Lazy%601.Value%2A> プロパティは読み取り専用です。  例外のキャッシュを有効にしている場合、この不変性は、例外の動作にも当てはまります。  限定的に初期化されたオブジェクトで、例外のキャッシュが有効になっており、<xref:System.Lazy%601.Value%2A> プロパティに最初にアクセスしたときにそのオブジェクトの初期化メソッドから例外がスローされた場合、後で <xref:System.Lazy%601.Value%2A> プロパティにアクセスしようとした場合も常に同じ例外がスローされます。  つまり、マルチスレッドのシナリオでも、ラップされた型のコンストラクターが再度呼び出されることはありません。  したがって、<xref:System.Lazy%601> オブジェクトで、いずれかのアクセスでは例外をスローし、その後のアクセスでは値を返すということはできません。  
  
 例外のキャッシュは、初期化メソッド \(`valueFactory` パラメーター\) を受け取る <xref:System.Lazy%601?displayProperty=fullName> コンストラクターを使用すると有効になります。たとえば、`Lazy(T)(Func(T))` コンストラクターを使用すると有効になります。  コンストラクターが <xref:System.Threading.LazyThreadSafetyMode> の値 \(`mode` パラメーター\) も受け取る場合は、<xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> または <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> を指定します。  初期化メソッドを指定すると、これら 2 つのモードで例外のキャッシュが有効になります。  初期化メソッドは非常に簡単なものにできます。  たとえば、`T` の既定のコンストラクター \(C\# では `new Lazy<Contents>(() => new Contents(), mode)`、Visual Basic では `New Lazy(Of Contents)(Function() New Contents())`\) を呼び出すことができます。  初期化メソッドを指定しない <xref:System.Lazy%601?displayProperty=fullName> コンストラクターを使用する場合、`T` の既定のコンストラクターによってスローされる例外はキャッシュされません。  詳細については、<xref:System.Threading.LazyThreadSafetyMode> 列挙体の解説を参照してください。  
  
> [!NOTE]
>  `isThreadSafe` コンストラクターのパラメーターが `false` に設定されている、または `mode` コンストラクターのパラメーターが <xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> に設定されている <xref:System.Lazy%601> オブジェクトを作成する場合は、シングル スレッドから <xref:System.Lazy%601> オブジェクトにアクセスするか、独自に同期を行う必要があります。  これは、例外のキャッシュを含む、オブジェクトのあらゆる面に当てはまります。  
  
 前のセクションで説明したように、<xref:System.Threading.LazyThreadSafetyMode?displayProperty=fullName> を指定して作成した <xref:System.Lazy%601> オブジェクトでは、例外の処理が異なります。  <xref:System.Threading.LazyThreadSafetyMode> を指定すると、<xref:System.Lazy%601> インスタンスを初期化する際に、複数のスレッドが競合します。  この場合、例外はキャッシュされず、<xref:System.Lazy%601.Value%2A> プロパティへのアクセス試行は、初期化が成功するまで続行されます。  
  
 次の表に、<xref:System.Lazy%601> コンストラクターによる例外のキャッシュの制御方法の概要を示します。  
  
|コンストラクター|スレッド セーフ モード|初期化メソッドを使用する|例外がキャッシュされる|  
|--------------|------------------|------------------|-----------------|  
|Lazy\(T\)\(\)|\(<xref:> System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?qualifyHint=False&autoUpgrade=True\)|No|No|  
|Lazy\(T\)\(Func\(T\)\)|\(<xref:> System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?qualifyHint=False&autoUpgrade=True\)|Yes|Yes|  
|Lazy\(T\)\(Boolean\)|`True` \(<xref:> System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?qualifyHint=False&autoUpgrade=True\) または `false` \(<xref:> System.Threading.LazyThreadSafetyMode.None?qualifyHint=False&autoUpgrade=True\)|No|No|  
|Lazy\(T\)\(Func\(T\), Boolean\)|`True` \(<xref:> System.Threading.LazyThreadSafetyMode.ExecutionAndPublication?qualifyHint=False&autoUpgrade=True\) または `false` \(<xref:> System.Threading.LazyThreadSafetyMode.None?qualifyHint=False&autoUpgrade=True\)|Yes|Yes|  
|Lazy\(T\)\(LazyThreadSafetyMode\)|ユーザー指定|No|No|  
|Lazy\(T\)\(Func\(T\), LazyThreadSafetyMode\)|ユーザー指定|Yes|ユーザーが <xref:> System.Threading.LazyThreadSafetyMode.PublicationOnly?qualifyHint=False&autoUpgrade=True を指定した場合は×、それ以外の場合は○。|  
  
## 限定的に初期化されたプロパティの実装  
 限定的な初期化を使用してパブリック プロパティを実装するには、プロパティのバッキング フィールドを <xref:System.Lazy%601> として定義し、<xref:System.Lazy%601.Value%2A> プロパティをそのプロパティの `get` アクセサーから返します。  
  
 [!code-csharp[Lazy#5](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#5)]
 [!code-vb[Lazy#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#5)]  
  
 <xref:System.Lazy%601.Value%2A> プロパティは読み取り専用です。したがって、このプロパティを公開するプロパティには `set` アクセサーはありません。  <xref:System.Lazy%601> オブジェクトによってサポートされる読み取り\/書き込みプロパティが必要な場合は、`set` アクセサーで新しい <xref:System.Lazy%601> オブジェクトを作成し、それをバッキング ストアに割り当てる必要があります。  `set` アクセサーでは、`set` アクセサーに渡された新しいプロパティ値を返すラムダ式を作成し、そのラムダ式を新しい <xref:System.Lazy%601> オブジェクトのコンストラクターに渡す必要があります。  <xref:System.Lazy%601.Value%2A> プロパティに次にアクセスしたときに、新しい <xref:System.Lazy%601> が初期化されます。その後、その <xref:System.Lazy%601.Value%2A> プロパティは、そのプロパティに代入された新しい値を返します。  このような複雑な処理を行うのは、<xref:System.Lazy%601> に組み込まれているマルチスレッド保護を維持するためです。  そのようにしないと、プロパティ アクセサーでは <xref:System.Lazy%601.Value%2A> プロパティから返された最初の値をキャッシュし、キャッシュされた値のみを変更するようになり、マルチスレッド保護を維持するには独自のスレッド セーフなコードを記述することが必要になります。  <xref:System.Lazy%601> オブジェクトでサポートされる読み取り\/書き込みプロパティによって必要な初期化処理が追加されるため、パフォーマンスが許容範囲を下回る可能性があります。  さらに、特定のシナリオでは、setter と getter との間の競合状態を回避するために、追加の調整が必要になることがあります。  
  
## スレッド ローカルな限定的な初期化  
 マルチスレッドの一部のシナリオでは、スレッドごとに独自のプライベート データを提供することもできます。  このようなデータのことを*スレッド ローカル データ*と呼びます。  .NET Framework Version 3.5 以前では、`ThreadStatic` 属性を静的変数に割り当てることでスレッド ローカルにすることができます。  ただし、`ThreadStatic` 属性を使用すると、明確でないエラーが発生する場合があります。  たとえば、次の例に示すように、基本的な初期化ステートメントでも、最初にアクセスしたスレッドでしか変数が初期化されないことがあります。  
  
 [!code-csharp[Lazy#6](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#6)]
 [!code-vb[Lazy#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#6)]  
  
 他のすべてのスレッドでは、既定値 \(0\) を使用して変数が初期化されます。  .NET Framework Version 4 では、代わりに <xref:System.Threading.ThreadLocal%601?displayProperty=fullName> 型を使用して、指定した <xref:System.Action%601> デリゲートによってすべてのスレッドで初期化されるインスタンス ベースのスレッド ローカルな変数を作成できます。  次の例では、`counter` にアクセスするすべてのスレッドで開始値が 1 と見なされます。  
  
 [!code-csharp[Lazy#7](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#7)]
 [!code-vb[Lazy#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#7)]  
  
 <xref:System.Threading.ThreadLocal%601> は、<xref:System.Lazy%601> とほぼ同じ方法でオブジェクトをラップしますが、本質的には次のように異なります。  
  
-   各スレッドでは、他のスレッドからはアクセスできない独自のプライベート データを使用してスレッド ローカル変数を初期化します。  
  
-   <xref:System.Threading.ThreadLocal%601.Value%2A?displayProperty=fullName> プロパティは読み書き可能であり、何回でも変更できます。  これは例外の反映にも影響し、たとえば、いずれかの `get` 操作では例外を発生させ、次の操作では値を正常に初期化ということができます。  
  
-   初期化デリゲートが指定されていない場合、<xref:System.Threading.ThreadLocal%601> では、ラップされた型をその型の既定値を使用して初期化します。  この点で、<xref:System.Threading.ThreadLocal%601> は <xref:System.ThreadStaticAttribute> 属性と一貫しています。  
  
 `ThreadLocal<int>` インスタンスにアクセスするすべてのスレッドで、データの独自の一意のコピーを取得する例を次に示します。  
  
 [!code-csharp[Lazy#9](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#9)]
 [!code-vb[Lazy#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#9)]  
  
## Parallel.For と ForEach のスレッド ローカル変数  
 <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=fullName> メソッドまたは <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=fullName> メソッドを使用してデータ ソースを並行して反復処理する場合、スレッド ローカル データのサポートが組み込まれたオーバーロードを使用できます。  これらのメソッドでは、データの作成、アクセス、およびクリーンアップにローカル デリゲートを使用することでスレッド ローカルが可能です。  詳細については、「[How to: Write a Parallel.For Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md)」および「[How to: Write a Parallel.ForEach Loop with Thread\-Local Variables](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md)」を参照してください。  
  
## オーバーヘッドが少ないシナリオでの限定的な初期化の使用  
 多数のオブジェクトを限定的に初期化する必要があるシナリオで、<xref:System.Lazy%601> では各オブジェクトをラップするために必要なメモリまたはコンピューティング リソースが多くなりすぎる場合があります。  また、限定的な初期化の公開方法について厳しい要件がある場合もあります。  そのような場合は、<xref:System.Threading.LazyInitializer?displayProperty=fullName> クラスの `static` \(Visual Basic では `Shared`\) メソッドを使用すると、<xref:System.Lazy%601> のインスタンスではラップせずに各オブジェクトを限定的に初期化できます。  
  
 次の例では、`Orders` オブジェクト全体を 1 つの <xref:System.Lazy%601> オブジェクトでラップするのではなく、それぞれの `Order` オブジェクトを必要になったときにのみ限定的に初期化したものとします。  
  
 [!code-csharp[Lazy#10](../../../samples/snippets/csharp/VS_Snippets_Misc/lazy/cs/cs_lazycodefile.cs#10)]
 [!code-vb[Lazy#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/lazy/vb/lazy_vb.vb#10)]  
  
 この例では、ループが繰り返されるたびに初期化プロシージャが呼び出されることに注意してください。  マルチスレッドのシナリオでは、初期化プロシージャを最初に呼び出したスレッドの値がすべてのスレッドで参照されます。  以降のスレッドも初期化プロシージャを呼び出しますが、それらの結果は使用されません。  このような潜在的な競合状態を受け入れられない場合は、ブール型の引数と同期オブジェクトを受け取る <xref:System.Threading.LazyInitializer.EnsureInitialized%2A?displayProperty=fullName> のオーバーロードを使用します。  
  
## 参照  
 [Managed Threading Basics](../../../docs/standard/threading/managed-threading-basics.md)   
 [Threads and Threading](../../../docs/standard/threading/threads-and-threading.md)   
 [Task Parallel Library \(TPL\)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)   
 [方法: オブジェクトの遅延初期化を実行する](../../../docs/framework/performance/how-to-perform-lazy-initialization-of-objects.md)