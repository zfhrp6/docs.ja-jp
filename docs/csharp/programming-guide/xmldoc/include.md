---
title: "&lt;include&gt; (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "include"
  - "<include>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<include> C# XML タグ"
  - "include C# XML タグ"
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# &lt;include&gt; (C# プログラミング ガイド)
## 構文  
  
```  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### パラメーター  
 `filename`  
 ドキュメントを含む XML ファイルの名前。  ファイル名にパスを指定することもできます。  `filename` は、単一引用符 \(' '\) で囲みます。  
  
 `tagpath`  
 `filename` のタグのパス。その後ろにタグの `name` を指定します。  パスは、単一引用符 \(' '\) で囲みます。  
  
 `name`  
 タグの名前指定子。その後ろにコメントを指定します。`name` には `id` を指定します。  
  
 `id`  
 タグの ID。その後ろにコメントを指定します。  ID は、二重引用符 \(" "\) で囲みます。  
  
## 解説  
 \<include\> タグを使用すると、ソース コード内の型およびメンバーの説明として、別のファイル内のコメントを参照できます。  これはソース コードのファイルにドキュメント コメントを直接記述しない方法です。  ドキュメントを別のファイル内に置くと、ソース コードとは別にドキュメントにソース管理を適用できます。  このため、あるユーザーがソース コード ファイルをチェックアウトし、別のユーザーがドキュメント ファイルをチェックアウトできます。  
  
 \<include\> タグは、XML の XPath 構文を使用します。  \<include\> タグのカスタマイズ方法については、XPath に関するドキュメントを参照してください。  
  
## 使用例  
 複数ファイルの例を次に示します。  最初のファイルは、次のように \<include\> タグを使用しています。  
  
 [!code-cs[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 2 番目のファイル xml\_include\_tag.doc には、次のドキュメント コメントが記述されています。  
  
```  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## プログラムの出力  
 次の出力は、「`/doc:DocFileName.xml.`」というコマンド ラインを使用して Test クラスと Test2 クラスをコンパイルしたときに生成されます。Visual Studio では、XML ドキュメント コメントのオプションはプロジェクト デザイナーの \[ビルド\] ペインで指定します。  C\# コンパイラは、\<include\> タグを認識すると、現在のソース ファイルではなく xml\_include\_tag.doc でドキュメント コメントを検索します。  次に、コンパイラは DocFileName.xml を生成します。このファイルが [Sandcastle](http://go.microsoft.com/fwlink/?LinkId=124061) などのドキュメント ツールで使用されて、最終的なドキュメントが生成されます。  
  
```  
<?xml version="1.0"?>   
<doc>   
    <assembly>   
        <name>xml_include_tag</name>   
    </assembly>   
    <members>   
        <member name="T:Test">   
            <summary>   
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)