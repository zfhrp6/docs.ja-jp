---
title: "&lt;include&gt; (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- include
- <include>
dev_langs:
- CSharp
helpviewer_keywords:
- <include> C# XML tag
- include C# XML tag
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: df0438dd742db802bb0f935d840006236d5d9bf9
ms.openlocfilehash: 0cabcc25c4e35027c600e4af2bccfad7f9db1514
ms.contentlocale: ja-jp
ms.lasthandoff: 08/29/2017

---
# <a name="ltincludegt-c-programming-guide"></a>&lt;include&gt; (C# プログラミング ガイド)
## <a name="syntax"></a>構文  
  
```xml  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### <a name="parameters"></a>パラメーター  
 `filename`  
 文書を含む XML ファイルの名前。 ファイル名をパスで修飾することができます。 `filename` を単一引用符 (' ') で囲みます。  
  
 `tagpath`  
 タグ `name` につながる `filename` 内のタグのパス。 パスを単一引用符 (' ') で囲みます。  
  
 `name`  
 コメントの前に配置するタグの名前指定子。`name` には `id` が指定されます。  
  
 `id`  
 コメントの前に配置するタグの ID。 ID は二重引用符 (" ") で囲みます。  
  
## <a name="remarks"></a>コメント  
 \<include> タグを使用して、ソース コード内の型とメンバーを記述する別のファイル内のコメントを参照することができます。 これは文書化のコメントをソース コード ファイル内に直接配置する方法の代替です。 別のファイルにドキュメントを配置することで、ソース コードから分離して、ソースの制御をドキュメントに適用できます。 1 人のユーザーがソース コード ファイルをチェックアウトし、他のユーザーがドキュメント ファイルをチェックアウトすることができます。  
  
 \<include> タグは XML XPath 構文を使用します。 \<include> の使用をカスタマイズする方法については、XPath に関するドキュメントを参照してください。  
  
## <a name="example"></a>例  
 これは、複数ファイルの例です。 \<include> を使用する最初のファイルを以下に記載します。  
  
 [!code-cs[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 2 番目のファイル xml_include_tag.doc には、次のドキュメントのコメントが含まれています。  
  
```xml  
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
  
## <a name="program-output"></a>プログラムの出力  
 コマンド ライン `/doc:DocFileName.xml.` で Test および Test2 クラスをコンパイルするときに、次の出力が生成されます。Visual Studio では、プロジェクト デザイナーの [ビルド] ウィンドウで、XML ドキュメント コメントのオプションを指定します。 C# コンパイラが \<include> タグを認識すると、現在のソース ファイルではなく xml_include_tag.doc でドキュメントのコメントを検索します。 コンパイラは次に、DocFileName.xml を生成します。これは、最終的なドキュメントを生成するために、[Sandcastle](https://github.com/EWSoftware/SHFB) などのドキュメント ツールによって利用されます。  
  
```xml  
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
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [ドキュメント コメントとして推奨されるタグ](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)

