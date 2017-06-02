---
title: "方法: リフレクション出力を使用してジェネリック型を定義する | Microsoft Docs"
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
  - "ジェネリック [.NET Framework], 動的な型"
  - "ジェネリック [.NET Framework], リフレクション出力"
  - "リフレクション出力, ジェネリック型"
ms.assetid: 07d5f01a-7b5b-40ea-9b15-f21561098fe4
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法: リフレクション出力を使用してジェネリック型を定義する
このトピックでは、2 つの型パラメーターを持つ単純なジェネリック型を作成する方法、クラスの制約、インターフェイスの制約、および特殊な制約を型パラメーターに適用する方法、クラスの型パラメーターをパラメーターの型および戻り値の型として使用するメンバーを作成する方法について説明します。  
  
> [!IMPORTANT]
>  メソッドはジェネリック型に属し、その型の型パラメーターを使用するだけであるため、ジェネリックではありません。  メソッドがジェネリックになるのは、そのメソッドが独自の型パラメーター リストを持つ場合だけです。  この例のように、ジェネリック型のほとんどのメソッドはジェネリックではありません。  ジェネリック メソッドの出力の例については、「[方法: リフレクション出力を使用してジェネリック メソッドを定義する](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-method-with-reflection-emit.md)」を参照してください。  
  
### ジェネリック型を定義するには  
  
1.  `GenericEmitExample1` という名前の動的アセンブリを定義します。  この例では、アセンブリを実行し、ディスクに保存するため、<xref:System.Reflection.Emit.AssemblyBuilderAccess?displayProperty=fullName> を指定します。  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2.  動的モジュールを定義します。  アセンブリは、実行可能モジュールで構成されます。  単一モジュールのアセンブリの場合、モジュール名はアセンブリ名と同じであり、ファイル名はモジュール名に拡張子が付いたものです。  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3.  クラスを定義します。  この例では、クラスの名前は `Sample` です。  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4.  パラメーターの名前を格納している文字列の配列を <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=fullName> メソッドに渡して、`Sample` のジェネリック型パラメーターを定義します。  これにより、クラスはジェネリック型になります。  戻り値は、型パラメーターを表す <xref:System.Reflection.Emit.GenericTypeParameterBuilder> オブジェクトの配列で、出力されたコードで使用できます。  
  
     次のコードでは、`Sample` は型パラメーター `TFirst` と `TSecond` を持つジェネリック型になります。  コードを読みやすくするために、各 <xref:System.Reflection.Emit.GenericTypeParameterBuilder> を型パラメーターと同じ名前の変数に配置します。  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5.  型パラメーターに特殊な制約を追加します。  この例では、型パラメーター `TFirst` は、パラメーターなしのコンストラクターを持つ型で、参照型に制約されています。  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6.  オプションで、型パラメーターにクラスの制約とインターフェイスの制約を追加します。  この例では、型パラメーター `TFirst` は、変数 `baseType` に格納された <xref:System.Type> オブジェクトによって表される基本クラスから派生し、型が変数 `interfaceA` と `interfaceB` に格納されたインターフェイスを実装する型に制約されています。  これらの変数の宣言および割り当てについては、コード例を参照してください。  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7.  フィールドを定義します。  この例では、フィールドの型は型パラメーター `TFirst` で指定されます。  <xref:System.Reflection.Emit.GenericTypeParameterBuilder> は <xref:System.Type> から派生するため、型を使用できる場合はいつでもジェネリック型パラメーターを使用できます。  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8.  ジェネリック型の型パラメーターを使用するメソッドを定義します。  このようなメソッドが独自の型パラメーター リストを持たない限り、メソッドはジェネリックではありません。  次のコードでは、`TFirst` の配列を受け取り、その配列のすべての要素を格納する `List<TFirst>` \(Visual Basic では `List(Of TFirst)`\) を返す `static` メソッド \(Visual Basic では `Shared`\) を定義します。  このメソッドを定義するには、ジェネリック型の定義 `List<T>` で <xref:System.Type.MakeGenericType%2A> を呼び出して、`List<TFirst>` 型を作成する必要があります \(`typeof` 演算子 \(Visual Basic では `GetType`\) を使用してジェネリック型の定義を取得する場合、`T` は省略されます\)。パラメーターの型は、<xref:System.Type.MakeArrayType%2A> メソッドを使用して作成されます。  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. メソッド本体を出力します。  メソッド本体は、入力配列をスタックに読み込む 3 つのオペコードで構成され、`IEnumerable<TFirst>` \(入力要素をリストに配置するすべての処理を実行\) を受け取る `List<TFirst>` コンストラクターを呼び出し、返されます \(新しい <xref:System.Collections.Generic.List%601> オブジェクトをスタックに残します\)。  このコードの出力の困難な部分は、コンストラクターの取得です。  
  
     <xref:System.Type.GetConstructor%2A> メソッドは <xref:System.Reflection.Emit.GenericTypeParameterBuilder> でサポートされていないため、`List<TFirst>` のコンストラクターを直接取得することはできません。  まず、ジェネリック型の定義 `List<T>` のコンストラクターを取得し、次に、このコンストラクターを `List<TFirst>` の対応するコンストラクターに変換するメソッドを呼び出す必要があります。  
  
     このコード例で使用するコンストラクターは、`IEnumerable<T>` を受け取ります。  ただし、これは <xref:System.Collections.Generic.IEnumerable%601> ジェネリック インターフェイスのジェネリック型の定義ではない点に注意してください。代わりに、`List<T>` の型パラメーター `T` を、`IEnumerable<T>` の型パラメーター `T` と置き換える必要があります \(両方の型が `T` という名前の型パラメーターを持つというだけで、わかりづらいように思われます。  このコード例で、`TFirst` と `TSecond` という名前を使用しているのはそのためです\)。コンストラクターの引数の型を取得するには、ジェネリック型の定義 `IEnumerable<T>` から開始し、`List<T>` の 1 つ目のジェネリック型パラメーターで <xref:System.Type.MakeGenericType%2A> を呼び出します。  コンストラクターの引数リストは、配列 \(この場合は引数を 1 つだけ持つ配列\) として渡す必要があります。  
  
    > [!NOTE]
    >  ジェネリック型の定義は、C\# の `typeof` 演算子を使用する場合は `IEnumerable<>` として表し、Visual Basic の `GetType` 演算子を使用する場合は `IEnumerable(Of )` として表します。  
  
     これで、ジェネリック型の定義で <xref:System.Type.GetConstructor%2A> を呼び出して、`List<T>` のコンストラクターを取得できるようになりました。  このコンストラクターを `List<TFirst>` の対応するコンストラクターに変換するには、`List<TFirst>` および `List<T>` のコンストラクターを静的 <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=fullName> メソッドに渡します。  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. 型を作成し、ファイルを保存します。  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. メソッドを呼び出します。  `ExampleMethod` はジェネリックではありませんが、属する型はジェネリックです。したがって、呼び出すことのできる <xref:System.Reflection.MethodInfo> を取得するためには、`Sample` の型定義から構築された型を作成する必要があります。  構築された型は、`Example` クラスを使用します。このクラスは参照型であり、既定のパラメーターなしのコンストラクターと、`TSecond` の制約を満たす `ExampleDerived` クラスを持つため、`TFirst` の制約を満たしています \(`ExampleDerived` のコードは、プログラム例のセクションにあります\)。この 2 つの型は、<xref:System.Type.MakeGenericType%2A> に渡されて、構築された型を作成します。  次に、<xref:System.Type.GetMethod%2A> メソッドを使用して <xref:System.Reflection.MethodInfo> が取得されます。  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. 次のコードでは、`Example` オブジェクトの配列を作成し、この配列を呼び出されるメソッドの引数を表す <xref:System.Object> 型の配列に配置し、[Invoke\(Object, Object\<xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> メソッドに渡します。  <xref:System.Reflection.MethodBase.Invoke%2A> メソッドは `static` であるため、このメソッドの最初の引数は null 参照です。  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## 使用例  
 基本クラスと 2 つのインターフェイスと共に、`Sample` という名前のクラスを定義するコード例を次に示します。  このプログラムは、`Sample` の 2 つのジェネリック型パラメーターを定義し、これをジェネリック型にします。  型をジェネリックにするのは、型パラメーターだけです。  このプログラムでは、型パラメーターの定義の前後にテスト メッセージを表示することによってこれを示します。  
  
 型パラメーター `TSecond` を使用して、基本クラスとインターフェイスを使用するためのクラスの制約とインターフェイスの制約を示し、型パラメーター `TFirst` を使用して特殊な制約を示します。  
  
 このコード例では、フィールドの種類およびメソッドのパラメーターの型と戻り値の型にクラスの型パラメーターを使用して、フィールドとメソッドを定義します。  
  
 `Sample` クラスが作成されると、メソッドが呼び出されます。  
  
 プログラムには、ジェネリック型の情報を示すメソッドと、型パラメーターの特殊な制約を示すメソッドが含まれています。  これらのメソッドを使用して、完成した `Sample` クラスの情報を表示します。  
  
 このプログラムでは、完了したモジュールを `GenericEmitExample1.dll` という名前でディスクに保存します。したがって、[Ildasm.exe \(IL 逆アセンブラー\)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) でこれを開き、`Sample` クラスの MSIL をチェックできます。  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## コードのコンパイル  
  
-   このコードには、コンパイルに必要な C\# の `using` ステートメント \(Visual Basic では `Imports`\) が含まれています。  
  
-   追加のアセンブリ参照は不要です。  
  
-   コマンド ラインで csc.exe、vbc.exe、または cl.exe を使用して、コードをコンパイルします。  Visual Studio でコードをコンパイルするには、コンソール アプリケーション プロジェクト テンプレートの中にコードを配置します。  
  
## 参照  
 <xref:System.Reflection.Emit.GenericTypeParameterBuilder>   
 [Using Reflection Emit](http://msdn.microsoft.com/ja-jp/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)   
 [Reflection Emit Dynamic Assembly Scenarios](http://msdn.microsoft.com/ja-jp/e1cc6750-e20f-473b-bb4e-f43bc66aecce)