---
title: "型の動的な読み込みおよび使用 | Microsoft Docs"
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
  - "動的な読み込みおよび使用 (型の)"
  - "事前バインディング"
  - "暗黙の遅延バインディング"
  - "遅延バインディング, 遅延バインディングの概要"
  - "リフレクション, 動的な使用 (型の)"
ms.assetid: db985bec-5942-40ec-b13a-771ae98623dc
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# 型の動的な読み込みおよび使用
リフレクションは、[!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] や JScript などの言語コンパイラで使用されるインフラストラクチャを提供することにより、暗黙の遅延バインディングを実装します。  バインディングとは、一意に指定された型に対応する宣言 \(つまり、実装\) を特定するプロセスのことです。  このプロセスがコンパイル時でなく実行時に発生する場合、遅延バインディングと呼びます。  [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)] では、コード内で暗黙の遅延バインディングを使用できます。Visual Basic コンパイラは、オブジェクトの型を取得するためにリフレクションを使用するヘルパー メソッドを呼び出します。  ヘルパー メソッドに渡された引数によって、実行時に適切なメソッドが呼び出されます。  ヘルパー メソッドに渡される引数は、そのメソッド呼び出しの対象であるインスタンス \(オブジェクト\)、呼び出すメソッドの名前 \(文字列\)、および呼び出すメソッドに渡す引数 \(オブジェクト配列\) です。  
  
 Visual Basic コンパイラが暗黙にリフレクションを使用して、コンパイル時に型が不明であるオブジェクトに対してメソッドを呼び出す例を次に示します。  **HelloWorld** クラスは、**PrintHello** メソッドを持っています。**PrintHello** メソッドは、渡されたテキストに "Hello World" という文字を連結して出力します。  この例で呼び出される **PrintHello** メソッドは、実際には、<xref:System.Type.InvokeMember%2A?displayProperty=fullName> です。Visual Basic コードでは、オブジェクト \(helloObj\) の型が、実行時 \(遅延バインディング\) ではなく、コンパイル時 \(事前バインディング\) に既にわかっていた場合と同様に、**PrintHello** メソッドを呼び出すことができます。  
  
```  
Imports System  
Module Hello  
    Sub Main()  
        ' Sets up the variable.  
        Dim helloObj As Object  
        ' Creates the object.  
        helloObj = new HelloWorld()  
        ' Invokes the print method as if it was early bound  
        ' even though it is really late bound.  
        helloObj.PrintHello("Visual Basic Late Bound")  
    End Sub  
End Module  
```  
  
## カスタム バインディング  
 リフレクションは、遅延バインディングのためにコンパイラによって暗黙に使用されるだけでなく、遅延バインディングを行うためにコード内で明示的に使用することもできます。  
  
 [共通言語ランタイム](../../../docs/standard/clr.md)は、複数のプログラミング言語をサポートしています。バインディング規則は、言語ごとに異なります。  事前バインディングの場合、バインディングはコード ジェネレーターによって完全に制御できます。  ただし、リフレクションによる遅延バインディングでは、カスタマイズしたバインディングによって制御する必要があります。  <xref:System.Reflection.Binder> クラスは、メンバー選択および呼び出しのカスタム コントロールを提供します。  
  
 カスタム バインディングを使用すると、実行時にアセンブリを読み込み、そのアセンブリ内の型についての情報を取得し、必要な型を指定し、その後でメソッドを呼び出したり、その型のフィールドやプロパティにアクセスできます。  この方法は、コンパイル時にオブジェクトの型を特定できない場合、たとえば、オブジェクトの型がユーザーの入力に依存するような場合に便利です。  
  
 引数の型変換のない単純なカスタム バインダーの例を次に示します。  `Simple_Type.dll` のコードを、メインのコードの前に示してあります。  まず `Simple_Type.dll` をビルドし、プロジェクトのビルド時に、その参照を含めます。  
  
 [!code-cpp[Conceptual.Types.Dynamic#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source1.cpp#1)]
 [!code-csharp[Conceptual.Types.Dynamic#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source1.cs#1)]
 [!code-vb[Conceptual.Types.Dynamic#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source1.vb#1)]  
  
### InvokeMember と CreateInstance  
 型のメンバーを呼び出すには、<xref:System.Type.InvokeMember%2A?displayProperty=fullName> を使用します。  さまざまなクラスの **CreateInstance** メソッド \([System.Activator](frlrfSystemActivatorClassCreateInstanceTopic) および [System.Reflection.Assembly](frlrfSystemReflectionAssemblyClassCreateInstanceTopic) など\) は、指定された型の新しいインスタンスを作成する **InvokeMember** の特殊な形態のメソッドです。  **Binder** クラスは、これらのメソッドのオーバーロード解決や引数の強制変換のために使用されます。  
  
 引数の強制変換 \(型変換\) とメンバー選択の可能な 3 つの組み合わせの例を次に示します。  ケース 1 では、引数の強制変換やメンバー選択は不要です。  ケース 2 では、メンバー選択だけが必要です。  ケース 3 では、引数の強制変換だけが必要です。  
  
 [!code-cpp[Conceptual.Types.Dynamic#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.dynamic/cpp/source2.cpp#2)]
 [!code-csharp[Conceptual.Types.Dynamic#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.dynamic/cs/source2.cs#2)]
 [!code-vb[Conceptual.Types.Dynamic#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.dynamic/vb/source2.vb#2)]  
  
 オーバーロード解決は、同じ名前のメンバーを複数使用できる場合に必要です。  <xref:System.Reflection.Binder.BindToMethod%2A?displayProperty=fullName> メソッドおよび <xref:System.Reflection.Binder.BindToField%2A?displayProperty=fullName> メソッドは、単一のメンバーへのバインディングを解決します。  また、**Binder.BindToMethod** は、**get** プロパティ アクセサーおよび **set** プロパティ アクセサーを使用するプロパティ解決も提供します。  
  
 **BindToMethod** は、呼び出す <xref:System.Reflection.MethodBase> を返します。このような呼び出しが不可能な場合は、null 参照 \(Visual Basic では **Nothing**\) を返します。  **MethodBase** の戻り値は、*match* パラメーターに含める必要はありませんが、通常は含まれています。  
  
 ByRef 引数が存在する場合、呼び出し元はその引数を取得することが必要な場合があります。  ByRef 引数を取得するために、**BindToMethod** が引数配列を操作した場合、クライアントは、**Binder** を使用して、引数配列を元の形態に対応付けることができます。  引数配列を元の形態に対応付けるには、呼び出し元に対して引数の順序が変更されていないことを保証する必要があります。  引数が名前で渡された場合、**Binder** は、引数配列の最順序付けを行います。呼び出し元に返されるのは、並べ替えられた後の引数配列です。  詳細については、「<xref:System.Reflection.Binder.ReorderArgumentArray%2A?displayProperty=fullName>」を参照してください。  
  
 利用可能なメンバーのセットは、その型と任意の基本型に定義されているメンバーです。  [BindingFlags.NonPublic](frlrfSystemReflectionBindingFlagsClassTopic) が指定されている場合は、いずれかのアクセシビリティのメンバーがそのセットに返されます。  **BindingFlags.NonPublic** が指定されていない場合は、バインダーはアクセシビリティ規則を適用する必要があります。  **Public** または **NonPublic** バインディング フラグを指定するときは、**Instance** または **Static** バインディング フラグも指定する必要があります。指定しなかった場合、メンバーは返されません。  
  
 指定された名前のメンバーが 1 つしか存在しない場合は、コールバックは不要です。バインディングは、そのメソッドで実行されます。  コード例のケース 1 は、コールバックが不要な場合を示しています。使用可能な **PrintBob** メソッドが 1 つしか存在しないため、コールバックは不要です。  
  
 利用可能なセットに複数のメンバーが存在する場合は、そのすべてのメソッドが **BindToMethod** に返されます。BindToMethod は適切なメソッドを選択し、それを返します。  コード例のケース 2 では、**PrintValue** という名前のメソッドが 2 つあります。  **BindToMethod** を呼び出すと、適切なメソッドが選択されます。  
  
 <xref:System.Reflection.Binder.ChangeType%2A> は、実引数を選択されたメソッドの仮引数の型に変換する引数の強制変換 \(型変換\) を行います。  **ChangeType** は、型が正確に一致した場合でも、すべての引数について呼び出されます。  
  
 コード例のケース 3 では、値 "5.5" の **String** 型の実引数が、**Double** 型の仮引数のメソッドに渡されます。  呼び出しを成功させるには、文字列値 "5.5" を倍精度浮動小数点値に変換する必要があります。  この変換は、**ChangeType** によって実行されます。  
  
 **ChangeType** は、次の表に示すように、ロスのない型の強制変換、つまり、[拡大変換](../../../docs/standard/base-types/type-conversion.md)だけを行います。  
  
|変換元の型|変換先の型|  
|-----------|-----------|  
|任意の型|その基本型|  
|任意の型|実装するインターフェイス|  
|Char|UInt16、UInt32、Int32、UInt64、Int64、Single、Double|  
|Byte|Char、UInt16、Int16、UInt32、Int32、UInt64、Int64、Single、Double|  
|SByte|Int16、Int32、Int64、Single、Double|  
|UInt16|UInt32、Int32、UInt64、Int64、Single、Double|  
|Int16|Int32、Int64、Single、Double|  
|UInt32|UInt64、Int64、Single、Double|  
|Int32|Int64、Single、Double|  
|UInt64|Single、Double|  
|Int64|Single、Double|  
|Single|Double|  
|非参照型|参照の種類|  
  
 <xref:System.Type> クラスは、参照を特定のメンバーとして解決する **Binder** 型のパラメーターを使用する **Get** メソッドを持っています。  <xref:System.Type.GetConstructor%2A?displayProperty=fullName>、<xref:System.Type.GetMethod%2A?displayProperty=fullName> 、および <xref:System.Type.GetProperty%2A?displayProperty=fullName> は、現在の型の特定のメンバーに関するシグネチャ情報を提供して、そのメンバーを検索します。  該当するメソッドの指定されたシグネチャ情報を選択するために、<xref:System.Reflection.Binder.SelectMethod%2A?displayProperty=fullName> および <xref:System.Reflection.Binder.SelectProperty%2A?displayProperty=fullName> がコールバックされます。  
  
## 参照  
 <xref:System.Type.InvokeMember%2A?displayProperty=fullName>   
 <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>   
 [型情報の表示](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)   
 [.NET Framework における型変換](../../../docs/standard/base-types/type-conversion.md)