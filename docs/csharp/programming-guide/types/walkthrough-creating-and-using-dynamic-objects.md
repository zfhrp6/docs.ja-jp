---
title: "チュートリアル: 動的オブジェクトの作成と使用 (C# および Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "動的オブジェクト"
  - "動的オブジェクト [C#]"
  - "動的オブジェクト [Visual Basic]"
ms.assetid: 568f1645-1305-4906-8625-5d77af81e04f
caps.latest.revision: 22
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 22
---
# チュートリアル: 動的オブジェクトの作成と使用 (C# および Visual Basic)
動的オブジェクトは、コンパイル時ではなく実行時に、プロパティやメソッドなどのメンバーを公開します。  これにより、静的な型または形式が一致しない構造体を操作するためのオブジェクトを作成できます。  たとえば、有効な HTML マークアップの要素と属性の組み合わせを含めることが可能な HTML ドキュメント オブジェクト モデル \(DOM: Document Object Model\) を参照する動的オブジェクトを作成できます。  各 HTML ドキュメントは一意であるため、特定の HTML ドキュメントのメンバーは実行時に決定されます。  HTML 要素の属性を参照するための一般的な方法として、要素の `GetProperty` メソッドに属性の名前を渡す方法があります。  `<div id="Div1">` という HTML 要素の `id` 属性を参照するには、まず `<div>` 要素への参照を取得し、次に `divElement.GetProperty("id")` を使用します。  動的オブジェクトを使用する場合は、`id` 属性を `divElement.id` として参照できます。  
  
 動的オブジェクトを使用すると、IronPython や IronRuby などの動的言語に簡単にアクセスすることもできます。  動的オブジェクトを使用して、実行時に解釈される動的スクリプトを参照できます。  
  
 動的オブジェクトを参照するには、遅延バインディングを使用します。  C\# では、遅延バインディング オブジェクトの型を `dynamic` として指定します。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、遅延バインディング オブジェクトの型を `Object` として指定します。  詳細については、「[動的](../../../csharp/language-reference/keywords/dynamic.md)」および「[Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)」を参照してください。  
  
 カスタム動的オブジェクトを作成するには、<xref:System.Dynamic?displayProperty=fullName> 名前空間のクラスを使用します。  たとえば、<xref:System.Dynamic.ExpandoObject> を作成し、実行時に、このオブジェクトのメンバーを指定できます。  <xref:System.Dynamic.DynamicObject> クラスを継承する独自の型を作成することもできます。  これにより、<xref:System.Dynamic.DynamicObject> クラスのメンバーをオーバーライドして、実行時の動的な機能を提供できます。  
  
 このチュートリアルでは、次のタスクを行います。  
  
-   テキスト ファイルの内容をオブジェクトのプロパティとして動的に公開するカスタム オブジェクトを作成します。  
  
-   `IronPython` ライブラリを使用するプロジェクトを作成します。  
  
## 必須コンポーネント  
 このチュートリアルを実行するには、IronPython 2.6.1 for .NET 4.0 が必要です。  IronPython 2.6.1 for .NET 4.0 は、[CodePlex](http://go.microsoft.com/fwlink/?LinkId=187223) からダウンロードできます。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
## カスタム動的オブジェクトの作成  
 このチュートリアルで作成する最初のプロジェクトでは、テキスト ファイルの内容を検索するカスタムの動的オブジェクトを定義します。  検索するテキストは、動的プロパティの名前で指定します。  たとえば、呼び出し元のコードで `dynamicFile.Sample` が指定されている場合、動的クラスは、ファイル内で "Sample" で始まるすべての行を含む文字列のジェネリック リストを返します。  検索では、大文字と小文字が区別されます。  動的クラスでは、2 つの省略可能な引数もサポートされています。  1 つ目の引数は、検索オプションの列挙値で、動的クラスが行の先頭、末尾、または任意の位置での一致を検索する必要があることを指定します。  2 つ目の引数は、動的クラスによって検索の前に各行から先頭と末尾の空白が削除される必要があることを指定します。  たとえば、呼び出し元のコードで `dynamicFile.Sample(StringSearchOption.Contains)` が指定されている場合、動的クラスは行の任意の位置にある "Sample" を検索します。  呼び出し元のコードで `dynamicFile.Sample(StringSearchOption.StartsWith, false)` が指定されている場合、動的クラスは各行の先頭で "Sample" を検索します。このとき、行の先頭と末尾にある空白は削除しません。  動的クラスの既定の動作では、各行の先頭での一致が検索され、先頭と末尾にある空白が削除されます。  
  
#### カスタムの動的クラスを作成するには  
  
1.  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] を起動します。  
  
2.  **\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
3.  **\[新しいプロジェクト\]** ダイアログ ボックスの **\[プロジェクトの種類\]** ペインで、**\[Windows\]** が選択されていることを確認します。  **\[テンプレート\]** ペインの **\[コンソール アプリケーション\]** を選択します。  **\[名前\]** ボックスに「`DynamicSample`」と入力し、**\[OK\]** をクリックします。  新しいプロジェクトが作成されます。  
  
4.  DynamicSample プロジェクトを右クリックし、**\[追加\]** をポイントして、**\[クラス\]** をクリックします。  **\[名前\]** ボックスに「`ReadOnlyFile`」と入力し、**\[OK\]** をクリックします。  ReadOnlyFile クラスを含む新しいファイルが追加されます。  
  
5.  ReadOnlyFile.cs ファイルまたは ReadOnlyFile.vb ファイルの先頭に次のコードを追加して、<xref:System.IO?displayProperty=fullName> 名前空間と <xref:System.Dynamic?displayProperty=fullName> 名前空間をインポートします。  
  
     [!code-cs[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/csharp/dynamicwalkthroughcs/readonlyfile.cs#1)]
     [!code-vb[VbDynamicWalkthrough#1](../../../csharp/programming-guide/types/codesnippet/visualbasic/dynamicwalkthrough/readonlyfile.vb#1)]  
  
6.  カスタムの動的オブジェクトは、列挙値を使用して検索条件を確認します。  class ステートメントの前に、次の列挙型定義を追加します。  
  
     [!code-cs[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/csharp/dynamicwalkthroughcs/readonlyfile.cs#2)]
     [!code-vb[VbDynamicWalkthrough#2](../../../csharp/programming-guide/types/codesnippet/visualbasic/dynamicwalkthrough/readonlyfile.vb#2)]  
  
7.  次のコード例に示すように、`DynamicObject` クラスを継承するように class ステートメントを更新します。  
  
     [!code-cs[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/csharp/dynamicwalkthroughcs/readonlyfile.cs#3)]
     [!code-vb[VbDynamicWalkthrough#3](../../../csharp/programming-guide/types/codesnippet/visualbasic/dynamicwalkthrough/readonlyfile.vb#3)]  
  
8.  `ReadOnlyFile` クラスに次のコードを追加して、ファイル パスのプライベート フィールドと `ReadOnlyFile` クラスのコンストラクターを定義します。  
  
     [!code-cs[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/csharp/dynamicwalkthroughcs/readonlyfile.cs#4)]
     [!code-vb[VbDynamicWalkthrough#4](../../../csharp/programming-guide/types/codesnippet/visualbasic/dynamicwalkthrough/readonlyfile.vb#4)]  
  
9. `ReadOnlyFile` クラスに次の `GetPropertyValue` メソッドを追加します。  `GetPropertyValue` メソッドは、入力として検索条件を受け取り、テキスト ファイル内でその検索条件に一致する行を返します。  `ReadOnlyFile` クラスによって提供される動的メソッドは  `GetPropertyValue` メソッドを呼び出して、それぞれの結果を取得します。  
  
     [!code-cs[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/csharp/dynamicwalkthroughcs/readonlyfile.cs#5)]
     [!code-vb[VbDynamicWalkthrough#5](../../../csharp/programming-guide/types/codesnippet/visualbasic/dynamicwalkthrough/readonlyfile.vb#5)]  
  
10. `GetPropertyValue` メソッドの後に次のコードを追加して、<xref:System.Dynamic.DynamicObject> クラスの <xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドをオーバーライドします。  動的クラスのメンバーが引数なしで要求されると、<xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドが呼び出されます。  `binder` 引数は参照先メンバーに関する情報を含み、`result` 引数は指定したメンバーについて返された結果を参照します。  <xref:System.Dynamic.DynamicObject.TryGetMember%2A> メソッドは、要求されたメンバーが存在する場合には `true` を返すブール値を返し、それ以外の場合には `false` を返すブール値を返します。  
  
     [!code-cs[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/csharp/dynamicwalkthroughcs/readonlyfile.cs#6)]
     [!code-vb[VbDynamicWalkthrough#6](../../../csharp/programming-guide/types/codesnippet/visualbasic/dynamicwalkthrough/readonlyfile.vb#6)]  
  
11. `TryGetMember` メソッドの後に次のコードを追加して、<xref:System.Dynamic.DynamicObject> クラスの <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドをオーバーライドします。  動的クラスのメンバーが引数付きで要求されると、<xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドが呼び出されます。  `binder` 引数は参照先メンバーに関する情報を含み、`result` 引数は指定したメンバーについて返された結果を参照します。  `args` 引数は、メンバーに渡される引数の配列を含みます。  <xref:System.Dynamic.DynamicObject.TryInvokeMember%2A> メソッドは、要求されたメンバーが存在する場合には `true` を返すブール値を返し、それ以外の場合には `false` を返すブール値を返します。  
  
     `TryInvokeMember` メソッドのカスタム バージョンは、1 つ目の引数が、前の手順で定義した `StringSearchOption` 列挙体に含まれるいずれかの値であることを求めます。  `TryInvokeMember` メソッドは、2 つ目の引数がブール値であることを求めます。  これらの引数のいずれかまたは両方が有効な値であれば、これらの引数は `GetPropertyValue` メソッドに渡され、結果が取得されます。  
  
     [!code-cs[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/csharp/dynamicwalkthroughcs/readonlyfile.cs#7)]
     [!code-vb[VbDynamicWalkthrough#7](../../../csharp/programming-guide/types/codesnippet/visualbasic/dynamicwalkthrough/readonlyfile.vb#7)]  
  
12. ファイルを保存して閉じます。  
  
#### サンプル テキスト ファイルを作成するには  
  
1.  DynamicSample プロジェクトを右クリックし、**\[追加\]** をポイントして、**\[新しい項目\]** をクリックします。  **\[インストールされたテンプレート\]** ペインで、**\[全般\]** を選択し、**\[テキスト ファイル\]** テンプレートを選択します。  **\[名前\]** ボックスで、既定の名前である TextFile1.txt をそのまま使用し、**\[追加\]** をクリックします。  プロジェクトに新しいテキスト ファイルが追加されます。  
  
2.  次のテキストを TextFile1.txt ファイルにコピーします。  
  
    ```  
    List of customers and suppliers  
  
    Supplier: Lucerne Publishing (http://www.lucernepublishing.com/)  
    Customer: Preston, Chris  
    Customer: Hines, Patrick  
    Customer: Cameron, Maria  
    Supplier: Graphic Design Institute (http://www.graphicdesigninstitute.com/)   
    Supplier: Fabrikam, Inc. (http://www.fabrikam.com/)   
    Customer: Seubert, Roxanne  
    Supplier: Proseware, Inc. (http://www.proseware.com/)   
    Customer: Adolphi, Stephan  
    Customer: Koch, Paul  
    ```  
  
3.  ファイルを保存して閉じます。  
  
#### カスタムの動的オブジェクトを使用するサンプル アプリケーションを作成するには  
  
1.  **ソリューション エクスプローラー**で、Module1.vb ファイル \([!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] を使用している場合\) または Program.cs ファイル \(Visual C\# を使用している場合\) をダブルクリックします。  
  
2.  次のコードを Main プロシージャに追加して、TextFile1.txt ファイルの `ReadOnlyFile` クラスのインスタンスを作成します。  このコードは、遅延バインディングを使用して動的メンバーを呼び出し、"Customer" という文字列を含むテキスト行を取得します。  
  
     [!code-cs[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/csharp/dynamicwalkthroughcs/program.cs#8)]
     [!code-vb[VbDynamicWalkthrough#8](../../../csharp/programming-guide/types/codesnippet/visualbasic/dynamicwalkthrough/module1.vb#8)]  
  
3.  ファイルを保存し、Ctrl キーを押しながら F5 キーを押して、アプリケーションをビルドおよび実行します。  
  
## 動的言語ライブラリの呼び出し  
 このチュートリアルで作成する次のプロジェクトでは、動的言語である IronPython で記述されたライブラリにアクセスします。  このプロジェクトを作成するには、IronPython 2.6.1 for .NET 4.0 がインストールされている必要があります。  IronPython 2.6.1 for .NET 4.0 は、[CodePlex](http://go.microsoft.com/fwlink/?LinkId=187223) からダウンロードできます。  
  
#### カスタムの動的クラスを作成するには  
  
1.  [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] で、**\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスの **\[プロジェクトの種類\]** ペインで、**\[Windows\]** が選択されていることを確認します。  **\[テンプレート\]** ペインの **\[コンソール アプリケーション\]** を選択します。  **\[名前\]** ボックスに「`DynamicIronPythonSample`」と入力し、**\[OK\]** をクリックします。  新しいプロジェクトが作成されます。  
  
3.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] を使用している場合は、DynamicIronPythonSample プロジェクトを右クリックし、**\[プロパティ\]** をクリックします。  **\[参照設定\]** タブをクリックします。  **\[追加\]** ボタンをクリックします。  Visual C\# を使用している場合は、**ソリューション エクスプローラー**で **\[参照設定\]** フォルダーを右クリックし、**\[参照の追加\]** をクリックします。  
  
4.  **\[参照\]** タブで、IronPython ライブラリがインストールされているフォルダーを参照します。  たとえば、C:\\Program Files\\IronPython 2.6 for .NET 4.0 を参照します。  **IronPython.dll**、**IronPython.Modules.dll**、**Microsoft.Scripting.dll**、**Microsoft.Dynamic.dll** の各ライブラリを選択します。  **\[OK\]** をクリックします。  
  
5.  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] を使用している場合は、Module1.vb ファイルを編集します。  Visual C\# を使用している場合は、Program.cs ファイルを編集します。  
  
6.  ファイルの先頭に次のコードを追加して、IronPython ライブラリから `Microsoft.Scripting.Hosting` 名前空間と `IronPython.Hosting` 名前空間をインポートします。  
  
     [!code-cs[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/csharp/ironpythonsample/program.cs#1)]
     [!code-vb[VbDynamicWalkthroughIronPython#1](../../../csharp/programming-guide/types/codesnippet/visualbasic/ironpythonsample/module1.vb#1)]  
  
7.  Main メソッドに次のコードを追加して、IronPython ライブラリをホストする新しい `Microsoft.Scripting.Hosting.ScriptRuntime` オブジェクトを作成します。  `ScriptRuntime` オブジェクトは、IronPython ライブラリ モジュール random.py を読み込みます。  
  
     [!code-cs[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/csharp/ironpythonsample/program.cs#2)]
     [!code-vb[VbDynamicWalkthroughIronPython#2](../../../csharp/programming-guide/types/codesnippet/visualbasic/ironpythonsample/module1.vb#2)]  
  
8.  random.py モジュールを読み込むコードの後に、次のコードを追加して整数の配列を作成します。  この配列は、random.py モジュールの `shuffle` メソッドに渡されます。このメソッドは、配列内の値をランダムに並べ替えます。  
  
     [!code-cs[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/csharp/ironpythonsample/program.cs#3)]
     [!code-vb[VbDynamicWalkthroughIronPython#3](../../../csharp/programming-guide/types/codesnippet/visualbasic/ironpythonsample/module1.vb#3)]  
  
9. ファイルを保存し、Ctrl キーを押しながら F5 キーを押して、アプリケーションをビルドおよび実行します。  
  
## 参照  
 <xref:System.Dynamic?displayProperty=fullName>   
 <xref:System.Dynamic.DynamicObject?displayProperty=fullName>   
 [dynamic 型の使用](../../../csharp/programming-guide/types/using-type-dynamic.md)   
 [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)   
 [動的](../../../csharp/language-reference/keywords/dynamic.md)   
 [動的インターフェイス実装します \(ブログ\) を外部](http://go.microsoft.com/fwlink/?LinkId=230895)