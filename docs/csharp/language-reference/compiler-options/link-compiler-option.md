---
title: "/link (C# Compiler Options) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/l compiler option [C#]"
  - "/link compiler option [C#]"
  - "-l compiler option [C#]"
  - "EmbedInteropTypes"
  - "l compiler option [C#]"
  - "embed interop types [COM Interop]"
  - "-link compiler option [C#]"
  - "link compiler option [C#]"
ms.assetid: 00da70c6-9ea1-43c2-86f2-aa7f26c03475
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# /link (C# Compiler Options)
指定のアセンブリ内の COM 型情報をコンパイル中のプロジェクトで使用できるようにします。  
  
## 構文  
  
```  
/link:fileList  
// -or-  
/l:fileList  
```  
  
## Arguments  
 `fileList`  
 必須。  アセンブリのファイル名をコンマで区切ったリストです。  ファイル名に空白が含まれる場合は、二重引用符 \(" "\) で囲む必要があります。  
  
## 解説  
 `/link` オプションを使用すると、埋め込み型情報を含むアプリケーションを配置できます。  このアプリケーションは、ランタイム アセンブリを参照せずに、埋め込み型情報を実装するランタイム アセンブリ内の型を使用できます。  ランタイム アセンブリのバージョンが多数公開されている場合、埋め込み型情報を含むアプリケーションは、再コンパイルしなくても各種バージョンと共に使用できます。  例については、「[チュートリアル: マネージ アセンブリからの型の埋め込み](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
 `/link` オプションは、COM 相互運用機能を使用している場合に特に便利です。  COM 型を埋め込むと、ターゲット コンピューターにプライマリ相互運用機能アセンブリ \(PIA: Primary Interop Assembly\) がなくてもアプリケーションを実行できるようになります。  `/link` オプションを使用すると、コンパイラによって、COM 型情報が参照先の相互運用機能アセンブリから結果としてコンパイルされるコードに埋め込まれます。  COM 型は、CLSID \(GUID\) 値によって識別されます。  そのため、同じ CLSID 値を持つ同じ COM 型がインストールされているターゲット コンピューターでアプリケーションを実行できます。  たとえば、Microsoft Office を自動化するアプリケーションの例を考えてみます。  通常、Office のようなアプリケーションは異なるバージョン間で同じ CLSID 値を保持するので、.NET Framework 4 以降がターゲット コンピューターにインストールされていて参照先の COM 型に含まれるメソッド、プロパティ、またはイベントが作成アプリケーションで使用される限りは、そのアプリケーションで参照先の COM 型を使用できます。  
  
 `/link` オプションで埋め込まれるのは、インターフェイス、構造体、およびデリゲートだけです。  COM クラスの埋め込みはサポートされていません。  
  
> [!NOTE]
>  コードで埋め込み COM 型のインスタンスを作成する場合は、適切なインターフェイスを使用してインスタンスを作成する必要があります。  コクラスを使用して埋め込み COM 型のインスタンスを作成しようとすると、エラーが発生します。  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] で `/link` オプションを設定するには、アセンブリ参照を追加して、`Embed Interop Types` プロパティを **true** に設定します。  `Embed Interop Types` プロパティの既定値は **false** です。  
  
 別の COM アセンブリ \(アセンブリ B\) を参照する COM アセンブリ \(アセンブリ A\) にリンクする場合、次のいずれかの条件に該当するときは、アセンブリ B にもリンクする必要があります。  
  
-   アセンブリ A の型がアセンブリ B の型を継承しているか、アセンブリ B のインターフェイスを実装している場合。  
  
-   アセンブリ B の戻り値の型やパラメーターの型を持つフィールド、プロパティ、イベント、またはメソッドを呼び出す場合。  
  
 [\/reference](../../../csharp/language-reference/compiler-options/reference-compiler-option.md) コンパイラ オプションと同様に、`/link` コンパイラ オプションでは、頻繁に使用される [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] アセンブリを参照する Csc.rsp 応答ファイルが使用されます。  コンパイラで Csc.rsp ファイルを使用しない場合は、[\/noconfig](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md) コンパイラ オプションを使用します。  
  
 `/link` の省略形は `/l` です。  
  
## ジェネリックと埋め込み型  
 以下のセクションでは、相互運用型を埋め込むアプリケーションでジェネリック型を使用する場合の制限事項について説明します。  
  
### ジェネリック インターフェイス  
 相互運用機能アセンブリから埋め込まれたジェネリック インターフェイスは使用できません。  これを次の例に示します。  
  
 [!code-cs[VbLinkCompilerCS#1](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_1.cs)]  
  
### ジェネリック パラメーターを含む型  
 型が相互運用機能アセンブリから埋め込まれたジェネリック パラメーターを含む型は、その型が外部アセンブリからの型である場合は使用できません。  ただし、これはインターフェイスには当てはまりません。  たとえば、<xref:Microsoft.Office.Interop.Excel> アセンブリで定義されている <xref:Microsoft.Office.Interop.Excel.Range> インターフェイスについて考えてみます。  ライブラリによって <xref:Microsoft.Office.Interop.Excel> アセンブリから相互運用型が埋め込まれ、型が <xref:Microsoft.Office.Interop.Excel.Range> インターフェイスであるパラメーターを含むジェネリック型を返すメソッドが公開される場合は、次のコード例に示すように、そのメソッドがジェネリック インターフェイスを返す必要があります。  
  
 [!code-cs[VbLinkCompilerCS#2](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_2.cs)]  
[!code-cs[VbLinkCompilerCS#3](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_3.cs)]  
[!code-cs[VbLinkCompilerCS#4](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_4.cs)]  
  
 次の例では、クライアント コードで <xref:System.Collections.IList> ジェネリック インターフェイスを返すメソッドをエラーなしで呼び出すことができます。  
  
 [!code-cs[VbLinkCompilerCS#5](../../../csharp/language-reference/compiler-options/codesnippet/CSharp/link-compiler-option_5.cs)]  
  
## 使用例  
 ソース ファイル `OfficeApp.cs` と、`COMData1.dll` および `COMData2.dll` からの参照アセンブリをコンパイルし、`OfficeApp.exe` を生成する場合のコード例です。  
  
```c#  
csc /link:COMData1.dll,COMData2.dll /out:OfficeApp.exe OfficeApp.cs  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [チュートリアル: マネージ アセンブリからの型の埋め込み](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [\/reference \(Import Metadata\)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)   
 [\/noconfig \(Ignore csc.rsp\)](../../../csharp/language-reference/compiler-options/noconfig-compiler-option.md)   
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)   
 [相互運用性の概要](../../../csharp/programming-guide/interop/interoperability-overview.md)