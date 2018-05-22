---
title: '方法 : XML ドキュメント機能を使用する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML documentation [C#]
- C# language, XML documentation features
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
ms.openlocfilehash: 6c7e30d23868959145e8941057f1c633fe6e374e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-xml-documentation-features-c-programming-guide"></a>方法 : XML ドキュメント機能を使用する (C# プログラミング ガイド)
次の例では、ドキュメント化された型の基本的な概要について説明します。  
  
## <a name="example"></a>例  
 [!code-csharp[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 **// この .xml ファイルは、上記のコード サンプルで生成されました。**  
**\<?xml version="1.0"?>**  
**\<doc>**  
 **\<assembly>**  
 **\<name>xmlsample\</name>**  
 **\</assembly>**  
 **\<members>**  
 **\<member name="T:SomeClass">**  
 **\<summary>**  
 **Class level summary documentation goes here.\</summary>**  
 **\<remarks>**  
 **Longer comments can be associated with a type or member**  
 **through the remarks tag\</remarks>**  
 **\</member>**  
 **\<member name="F:SomeClass.m_Name">**  
 **\<summary>**  
 **Store for the name property\</summary>**  
 **\</member>**  
 **\<member name="M:SomeClass.#ctor">**  
 **\<summary>The class constructor.\</summary>**  
 **\</member>**  
 **\<member name="M:SomeClass.SomeMethod(System.String)">**  
 **\<summary>**  
 **Description for SomeMethod.\</summary>**  
 **\<param name="s"> Parameter description for s goes here\</param>**  
 **\<seealso cref="T:System.String">**  
 **You can use the cref attribute on any tag to reference a type or member**  
 **and the compiler will check that the reference exists. \</seealso>**  
 **\</member>**  
 **\<member name="M:SomeClass.SomeOtherMethod">**  
 **\<summary>**  
 **Some other method. \</summary>**  
 **\<returns>**  
 **Return results are described through the returns tag.\</returns>**  
 **\<seealso cref="M:SomeClass.SomeMethod(System.String)">**  
 **Notice the use of the cref attribute to reference a specific method \</seealso>**  
 **\</member>**  
 **\<member name="M:SomeClass.Main(System.String[])">**  
 **\<summary>**  
 **The entry point for the application.**  
 **\</summary>**  
 **\<param name="args"> A list of command line arguments\</param>**  
 **\</member>**  
 **\<member name="P:SomeClass.Name">**  
 **\<summary>**  
 **Name property \</summary>**  
 **\<value>**  
 **A value tag is used to describe the property value\</value>**  
 **\</member>**  
 **\</members>**  
**\</doc>**   
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例をコンパイルするには、次のコマンド行を入力します。  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 これによって作成される XML ファイル XMLsample.xml は、ブラウザーで、または TYPE コマンドを使って、表示できます。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 XML ドキュメントは、/// で始まります。 新しいプロジェクトを作成すると、開始の /// 行がいくつか自動的に挿入されます。 これらのコメントの処理にはいくつか制限があります。  
  
-   ドキュメントは整形式の XML である必要があります。 XML が整形式ではない場合は、警告が生成され、エラーが発生したことを示すコメントがドキュメント ファイルに追加されます。  
  
-   開発者は、独自のタグ セットを自由に作成できます。 推奨されるタグ セットがあります (「関連項目」セクションを参照)。 推奨されるタグの一部には特別な意味があります。  
  
    -   \<param> タグは、パラメーターの記述に使われます。 このタグがあると、コンパイラは、パラメーターが存在すること、およびすべてのパラメーターがドキュメントで記述されていることを確認します。 検証で問題がある場合、コンパイラは警告を生成します。  
  
    -   `cref` 属性は任意のタグにアタッチでき、コード要素への参照を提供します。 コンパイラは、このコード要素が存在することを確認します。 検証で問題がある場合、コンパイラは警告を生成します。 コンパイラは、`cref` 属性で記述されている型を探すとき、`using` ステートメントに従います。  
  
    -   \<summary> タグは、型またはメンバーに関する追加情報を表示するために、Visual Studio の IntelliSense によって使われます。  
  
        > [!NOTE]
        >  XML ファイルでは、型とメンバーに関する完全な情報は提供されません (たとえば、型の情報は含まれません)。 型またはメンバーの完全な情報を取得するには、ドキュメント ファイルと併せて、実際の型またはメンバーでリフレクションを使う必要があります。  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [/doc (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)  
 [XML ドキュメント コメント](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)
