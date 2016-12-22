---
title: "方法 : XML ドキュメント機能を使用する (C# プログラミング ガイド) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "XML ドキュメント [C#]"
  - "C# 言語、XML ドキュメント機能"
ms.assetid: 8f33917b-9577-4c9a-818a-640dbbb0b399
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 方法 : XML ドキュメント機能を使用する (C# プログラミング ガイド)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

次の例では、ドキュメント化された型の基本的な概要を説明します。  
  
## <a name="example"></a>例  
 [!code-cs[csProgGuideDocComments#15](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/how-to-use-the-xml-documentation-features_1.cs)]  
  
 **この .xml ファイルには、上記のコード サンプルが生成されます。**  
**\<? xml version =「1.0」ですか?>**  
**\< ドキュメント>**  
 **\< アセンブリ>**  
 **\< 名前>xmlsample \</name>**  
 **\</アセンブリ>**  
 **\< メンバー>**  
 **\< メンバー名 ="T:SomeClass">**  
 **\< 概要>**  
 **クラス レベルの概要ドキュメントがここに示します \</概要。>**  
 **\< 解説>**  
 **長いコメントは、型またはメンバーに関連付けることができます。**   
 **「解説」タグを \< remarks/>**  
 **\</メンバー>**  
 **\< メンバー name="F:SomeClass.m_Name">**  
 **\< 概要>**  
 **Name プロパティのストア \</概要>**  
 **\</メンバー>**  
 **\< メンバー名 ="M:SomeClass. #ctor">**  
 **\< 概要>クラスのコンス トラクター \</概要。>**   
 **\</メンバー>**  
 **\< メンバー name="M:SomeClass.SomeMethod(System.String)">**  
 **\< 概要>**  
 **説明を SomeMethod \</概要。>**  
 **\< param name ="s"> s のパラメーターの説明をここに挿入します \</パラメーター。>**  
 **\< seealso cref="T:System.String">**  
 **任意のタグの cref 属性を使用して、型またはメンバーを参照できます。**   
 **コンパイラは、参照が存在することを確認します。\</seealso>**  
 **\</メンバー>**  
 **\< メンバー name="M:SomeClass.SomeOtherMethod">**  
 **\< 概要>**  
 **その他の方法です。\< 概要/>**  
 **\< を返します>**  
 **返す結果を返しますタグ。 で説明しています \</returns。>**  
 **\< seealso cref="M:SomeClass.SomeMethod(System.String)">**  
 **特定のメソッドを参照する cref 属性の使用に注意してください \</seealso>**  
 **\</メンバー>**  
 **\< メンバー name="M:SomeClass.Main(System.String[])">**  
 **\< 概要>**  
 **アプリケーションのエントリ ポイント。**  
 **\< 概要/>**  
 **\< param name ="args"> コマンドライン引数のリスト \</パラメーター>**  
 **\</メンバー>**  
 **\< メンバー name="P:SomeClass.Name">**  
 **\< 概要>**  
 **Name プロパティ \</概要>**  
 **\< 値>**  
 **値タグを使用して、プロパティの値を説明 \</value>**  
 **\</メンバー>**  
 **\</メンバー>**  
**\</ドキュメント>**   
## <a name="compiling-the-code"></a>コードのコンパイル  
 例をコンパイルするには、次のコマンドラインを入力します。  
  
 `csc XMLsample.cs /doc:XMLsample.xml`  
  
 これにより、XML ファイルまたは型のコマンドを使用して、ブラウザーで表示できる XMLsample.xml が作成されます。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 XML ドキュメントは、///から始まります。 新しいプロジェクトを作成するときに、ウィザードは内のスターター線///を配置します。 これらのコメントの処理には、いくつかの制限があります。  
  
-   ドキュメントが整形式である XML です。 XML が整形式でない場合、警告を生成し、ドキュメント ファイルが、エラーが発生したことを示すコメントを記録します。  
  
-   開発者は、自由に独自のタグのセットを作成できます。 推奨されるタグ (参考資料」セクションを参照してください) の設定があります。 推奨されるタグの一部は、特別な意味を持っています。  
  
    -   \< Param> タグを使用して、パラメーターを説明します。 使用する場合、コンパイラは、パラメーターが存在して、すべてのパラメーターが、ドキュメントに記載されているを確認します。 検証に失敗した場合、コンパイラは警告を発します。  
  
    -    `cref` 属性は、コード要素への参照を提供する任意のタグに関連付けることができます。 コンパイラは、このコード要素が存在することを確認します。 検証に失敗した場合、コンパイラは警告を発します。 コンパイラはいずれかの `using` ステートメントで示される型を探すときに、 `cref` 属性です。  
  
    -   \< 概要> 型またはメンバーに関する追加情報を表示する Visual Studio での IntelliSense によってタグを使用します。  
  
        > [!NOTE]
        >  XML ファイルが、型とメンバーの完全な情報を提供していない (たとえば、任意の種類の情報を含まれません)。 型またはメンバーの完全な情報を取得するには、実際の型またはメンバーにリフレクションと一緒にドキュメント ファイルを使用する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [/doc (c# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [XML ドキュメントのコメント](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)