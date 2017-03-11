---
title: "XML ファイルの処理 (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "XML [C#], 処理"
  - "XML 処理 [C#]"
ms.assetid: 60c71193-9dac-4cd3-98c5-100bd0edcc42
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# XML ファイルの処理 (C# プログラミング ガイド)
コンパイラは、ドキュメントを生成するためにタグ付けされたコードの構成体ごとに、ID 文字列を生成します。  コードにタグを付ける方法については、「[ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)」を参照してください。ID 文字列によって、構成体は一意に識別されます。  XML ファイルを処理するプログラムは、ID 文字列を使用して、ドキュメントの適用対象となる .NET Framework メタデータ\/リフレクション項目を識別できます。  
  
 XML ファイルは、コードの階層的表現ではなく、要素ごとに生成された ID のあるフラットなリストです。  
  
 コンパイラは、次の規則に基づいて ID 文字列を生成します。  
  
-   空白は含めません。  
  
-   ID 文字列の最初の部分には、単一の文字とコロンで識別されるメンバーの種類を示します。  使用されるメンバー型は次のとおりです。  
  
    |文字|Description|  
    |--------|-----------------|  
    |N|namespace<br /><br /> 名前空間にはドキュメント コメントを追加できませんが、サポートされている場合は、ドキュメント コメントへの cref 参照を作成できます。|  
    |T|型 : class、interface、struct、enum、delegate|  
    |F|field|  
    |P|プロパティ \(インデクサーまたはその他のインデックス付きプロパティを含む\)|  
    |M|メソッド \(コンストラクター、演算子などの特殊なメソッドを含む\)|  
    |E|event|  
    |\!|エラー文字列<br /><br /> エラーに続く文字列で、エラーの内容を示します。  C\# コンパイラは、解決できないリンクについてのエラー情報を生成します。|  
  
-   文字列の 2 番目の部分は、項目の完全限定名です。名前は、名前空間のルートから始まります。  項目の名前、項目が含まれている型、および名前空間は、ピリオドで区切られます。  名前自体にピリオドがある場合、名前のピリオドはハッシュ記号 \('\#'\) に置き換えられます。  項目の名前にはハッシュ記号がないことが前提です。  たとえば、String コンストラクターの完全限定名は、"System.String.\#ctor" になります。  
  
-   プロパティおよびメソッドについては、メソッドに引数がある場合は、引数のリストをかっこで囲み、メソッドに続けて指定します。  引数がない場合は、かっこはありません。  引数の区切り文字には、コンマを使用します。  各引数のエンコードは、次に示す .NET Framework のシグネチャでの引数のエンコーディング方法にそのまま従います。  
  
    -   基本型。  通常の型 \(ELEMENT\_TYPE\_CLASS または ELEMENT\_TYPE\_VALUETYPE\) は、型の完全限定名で表されます。  
  
    -   ELEMENT\_TYPE\_I4、ELEMENT\_TYPE\_OBJECT、ELEMENT\_TYPE\_STRING、ELEMENT\_TYPE\_TYPEDBYREF、  ELEMENT\_TYPE\_VOID など、組み込みの型は、対応する完全な型の完全修飾名で表されます。  たとえば、System.Int32 や System.TypedReference です。  
  
    -   ELEMENT\_TYPE\_PTR は、修飾される型に続けて '\*' と表されます。  
  
    -   ELEMENT\_TYPE\_BYREF は、修飾される型に続けて '@' と表されます。  
  
    -   ELEMENT\_TYPE\_PINNED は、修飾される型に続けて '^' と表されます。  C\# コンパイラでは生成されません。  
  
    -   ELEMENT\_TYPE\_CMOD\_REQ は、修飾される型に続けて "&#124;" と修飾子クラスの完全限定名で表されます。  C\# コンパイラでは生成されません。  
  
    -   ELEMENT\_TYPE\_CMOD\_OPT は、修飾される型に続けて "\!" と修飾子クラスの完全修飾名で表されます。  
  
    -   ELEMENT\_TYPE\_SZARRAY は、配列の要素型に続けて "\[\]" と表されます。  
  
    -   ELEMENT\_TYPE\_GENERICARRAY は、配列の要素型に続けて "\[?\]" と表されます。  C\# コンパイラでは生成されません。  
  
    -   ELEMENT\_TYPE\_ARRAY は、\[*lowerbound*:`size`,*lowerbound*:`size`\] の形式で表されます。ここで、コンマの個数はランク \-1 個であり、各次元の下限とサイズは明らかな場合は、10 進数で表されます。  下限またはサイズを、指定しない場合は省略します。  特定の次元で下限およびサイズが省略されている場合は、その次元の ':' も省略されます。  たとえば、ある 2 次元配列の下限が 1 で、サイズの指定がない場合は、\[1:,1:\] と表されます。  
  
    -   ELEMENT\_TYPE\_FNPTR は、"\=FUNC:`type`\(*signature*\)" と表されます。ここで、`type` は戻り値の型であり、*signature* はメソッドの引数です。  引数がない場合は、かっこが省略されます。  C\# コンパイラでは生成されません。  
  
     次に示すシグネチャ コンポーネントは、オーバーロードされるメソッドの区別には使用されることがないため、表されません。  
  
    -   呼び出し規約  
  
    -   戻り値の型  
  
    -   ELEMENT\_TYPE\_SENTINEL  
  
-   変換演算子 \(op\_Implicit および op\_Explicit\) だけは、上記のエンコードと同様に、メソッドの戻り値が '~' としてエンコードされ、それに続けて戻り値の型が表されます。  
  
-   ジェネリック型では、型の名前の後に、バック チック \(\`\)、ジェネリック型パラメーターの数を示す数値が順に続きます。  次に例を示します。  
  
     `<member name="T:SampleClass`2">` は、`public class SampleClass<T, U>` として定義されている型のタグです。  
  
     パラメーターとしてジェネリック型を受け取るメソッドでは、ジェネリック型パラメーターは、バック チック付きの数値 \(\`0、\`1 など\) として指定されます。  各数値は、型のジェネリック パラメーターに対する、インデックス番号が 0 から始まる配列表記を表しています。  
  
## 例  
 クラスおよびそのメンバーの ID 文字列が生成される例を次に示します。  
  
 [!code-cs[csProgGuidePointers#21](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/csharp/Pointers/Pointers.cs#21)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [\/doc \(Process Documentation Comments\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [XML ドキュメント コメント](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)