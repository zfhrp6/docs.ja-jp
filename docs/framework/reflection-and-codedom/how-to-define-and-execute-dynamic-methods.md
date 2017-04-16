---
title: "方法: 動的メソッドを定義および実行する | Microsoft Docs"
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
  - "動的メソッド"
  - "リフレクション出力, 動的メソッド"
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法: 動的メソッドを定義および実行する
単純な動的メソッドとクラスのインスタンスにバインドされた動的メソッドを定義し、実行する手順を次に示します。  動的メソッドの詳細については、<xref:System.Reflection.Emit.DynamicMethod> クラスに関するトピックおよび「[Reflection Emit Dynamic Method Scenarios](http://msdn.microsoft.com/ja-jp/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)」を参照してください。  
  
### 動的メソッドを定義および実行するには  
  
1.  メソッドを実行するために、デリゲート型を宣言します。  汎用デリゲートを使用して、宣言する必要のあるデリゲート型の数を最小限に抑えるよう考慮してください。  次のコードでは、`SquareIt` メソッドで使用できる 2 つのデリゲート型 \(1 つはジェネリック\) を宣言します。  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  動的メソッドのパラメーターの型を指定する配列を作成します。  この例では、唯一のパラメーターが `int` \(Visual Basic では `Integer`\) であるため、配列には要素は 1 つしかありません。  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  <xref:System.Reflection.Emit.DynamicMethod> を作成します。  この例では、メソッドの名前は `SquareIt` です。  
  
    > [!NOTE]
    >  動的メソッドに名前を付ける必要はありません。動的メソッドは名前で呼び出すことはできません。  複数の動的メソッドに同じ名前を付けることができます。  ただし、名前は呼び出し履歴に表示されるため、デバッグの際に役立つ場合があります。  
  
     戻り値の型は、`long` として指定します。  プログラム例を格納する `Example` クラスを含むモジュールにメソッドを関連付けます。  読み込むモジュールを指定できます。  動的メソッドは、モジュール レベルの `static` メソッド \(Visual Basic `Shared`\) と同様に機能します。  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  メソッド本体を出力します。  この例では、<xref:System.Reflection.Emit.ILGenerator> オブジェクトを使用して、MSIL \(Microsoft Intermediate Language\) を出力します。  また、<xref:System.Reflection.Emit.DynamicILInfo> オブジェクトをアンマネージ コード ジェネレーターと組み合わせて使用して、<xref:System.Reflection.Emit.DynamicMethod> のメソッド本体を出力することもできます。  
  
     この例の MSIL は、`int` である引数をスタックに読み込み、これを `long` に変換します。次に、`long` を複製し、2 つの数値を乗算します。  これにより、スタックには 2 乗された結果が残され、メソッドで実行する必要のあるすべてが返されます。  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> メソッドを呼び出して、動的メソッドを表す \(手順 1 で宣言した\) デリゲートのインスタンスを作成します。  デリゲートを作成すると、メソッドは完了します。メソッドにそれ以上変更を加えようとしても \(MSIL の追加など\) 無視されます。  次のコードでは、汎用デリゲートを使用して、デリゲートを作成し呼び出します。  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### オブジェクトにバインドされた動的メソッドを定義および実行するには  
  
1.  メソッドを実行するために、デリゲート型を宣言します。  汎用デリゲートを使用して、宣言する必要のあるデリゲート型の数を最小限に抑えるよう考慮してください。  次のコードでは、1 つのパラメーターと戻り値を持つ任意のメソッド、またはデリゲートがオブジェクトにバインドされている場合は 2 つのパラメーターと戻り値を持つメソッドの実行に使用できる汎用デリゲート型を宣言します。  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  動的メソッドのパラメーターの型を指定する配列を作成します。  メソッドを表すデリゲートをオブジェクトにバインドする場合、1 つ目のパラメーターは、デリゲートのバインド先となる型と一致する必要があります。  この例では、`Example` 型と `int` 型 \(Visual Basic では `Integer`\) の 2 つのパラメーターがあります。  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  <xref:System.Reflection.Emit.DynamicMethod> を作成します。  この例では、メソッドには名前はありません。  戻り値の型は、`int` \(Visual Basic では `Integer`\) として指定します。  このメソッドは、`Example` クラスのプライベート メンバーとプロテクト メンバーにアクセスできます。  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  メソッド本体を出力します。  この例では、<xref:System.Reflection.Emit.ILGenerator> オブジェクトを使用して、MSIL \(Microsoft Intermediate Language\) を出力します。  また、<xref:System.Reflection.Emit.DynamicILInfo> オブジェクトをアンマネージ コード ジェネレーターと組み合わせて使用して、<xref:System.Reflection.Emit.DynamicMethod> のメソッド本体を出力することもできます。  
  
     この例の MSIL は、`Example` クラスのインスタンスである 1 つ目の引数を読み込み、この引数を使用して、`int` 型のプライベート インスタンス フィールドの値を読み込みます。  2 つ目の引数が読み込まれ、この 2 つの数値が乗算されます。  この結果が `int` よりも大きい場合、値は切り捨てられ、上位ビットは破棄されます。  戻り値がスタックに配置されて、メソッドが返されます。  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> メソッド オーバーロードを呼び出して、動的メソッドを表す \(手順 1 で宣言した\) デリゲートのインスタンスを作成します。  デリゲートを作成すると、メソッドは完了します。メソッドにそれ以上変更を加えようとしても \(MSIL の追加など\) 無視されます。  
  
    > [!NOTE]
    >  <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> メソッドを複数回呼び出して、対象の型の他のインスタンスにバインドされたデリゲートを作成できます。  
  
     次のコードでは、プライベート テスト フィールドが 42 に設定された `Example` クラスの新しいインスタンスにメソッドをバインドします。  つまり、デリゲートが呼び出されるたびに、`Example` のインスタンスがメソッドの 1 つ目のパラメーターに渡されます。  
  
     メソッドの 1 つ目のパラメーターは、常に `Example` のインスタンスを受け取るため、`OneParameter` デリゲートが使用されます。  デリゲートの呼び出し時には、2 つ目のパラメーターだけが必要となります。  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## 使用例  
 単純な動的メソッドおよびクラスのインスタンスにバインドされた動的メソッドを次のコード例に示します。  
  
 この単純な動的メソッドは、32 ビット整数である引数を 1 つ受け取り、その整数の 2 乗を 64 ビットで返します。  汎用デリゲートを使用して、メソッドを呼び出します。  
  
 2 つ目の動的メソッドには、`Example` 型と `int` 型 \(Visual Basic では `Integer`\) の 2 つのパラメーターがあります。  動的メソッドが作成されると、`int` 型の引数を 1 つ持つ汎用デリゲートを使用して、`Example` のインスタンスにバインドされます。  メソッドの 1 つ目のパラメーターは、常に `Example` のバインドされたインスタンスを受け取るため、デリゲートは `Example` 型の引数を持ちません。  デリゲートの呼び出し時には、`int` 型の引数だけが提供されます。  動的メソッドは、`Example` クラスのプライベート フィールドにアクセスし、プライベート フィールドと `int` 型の引数の積を返します。  
  
 メソッドの実行に使用できるデリゲートを定義するコード例を次に示します。  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## コードのコンパイル  
  
-   このコードには、コンパイルに必要な C\# の `using` ステートメント \(Visual Basic では `Imports`\) が含まれています。  
  
-   追加のアセンブリ参照は不要です。  
  
-   コマンド ラインで csc.exe、vbc.exe、または cl.exe を使用して、コードをコンパイルします。  Visual Studio でコードをコンパイルするには、コンソール アプリケーション プロジェクト テンプレートの中にコードを配置します。  
  
## 参照  
 <xref:System.Reflection.Emit.DynamicMethod>   
 [Using Reflection Emit](http://msdn.microsoft.com/ja-jp/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)   
 [Reflection Emit Dynamic Method Scenarios](http://msdn.microsoft.com/ja-jp/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)