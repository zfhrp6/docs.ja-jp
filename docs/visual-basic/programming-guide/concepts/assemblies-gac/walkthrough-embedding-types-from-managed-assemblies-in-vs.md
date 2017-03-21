---
title: "チュートリアル: Visual Studio (Visual Basic) のアセンブリをマネージ型からの埋め込み |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 56ed12ba-adff-4e9c-a668-7fcba80c4795
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: adc58e081cd9b874a841d84b11d92cbffb6ba6b8
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-embedding-types-from-managed-assemblies-in-visual-studio-visual-basic"></a>チュートリアル: Visual Studio (Visual Basic) でのマネージ アセンブリから型の埋め込み
厳密な名前のマネージ アセンブリから型情報を埋め込む場合は、バージョンに依存しないを実現するために、アプリケーションの種類を疎結合できます。 つまり、バージョンごとに再コンパイルすることがなくマネージ ライブラリの複数のバージョンからの型を使用するプログラムを書き込むことができます。  
  
 型の埋め込みは COM 相互運用の Microsoft Office からのオートメーション オブジェクトを使用するアプリケーションなどでよく使用します。 型情報を埋め込むと、Microsoft Office の異なるコンピューター上の異なるバージョンを使用するプログラムの同じビルドができます。 ただし、完全に管理されたソリューションを埋め込み型を使用することもできます。  
  
 次の特性を持つアセンブリから型情報を埋め込むことができます。  
  
-   アセンブリは、少なくとも&1; つのパブリック インターフェイスを公開します。  
  
-   埋め込みのインターフェイスが付いた、`ComImport`属性と`Guid`属性 (および一意の GUID)。  
  
-   アセンブリが付いた、`ImportedFromTypeLib`属性または`PrimaryInteropAssembly`属性、およびアセンブリ レベル`Guid`属性です。 (既定では、Visual Basic プロジェクト テンプレートには、アセンブリ レベルが含まれて`Guid`属性です)。  
  
 埋め込むことができるパブリック インターフェイスを指定したら、それらのインターフェイスを実装するランタイム クラスを作成できます。 クライアント プログラムをパブリック インターフェイスと設定を含むアセンブリを参照することでデザイン時にこれらのインターフェイスの型情報を埋め込むことができますし、`Embed Interop Types`プロパティへの参照の`True`です。 これは、コマンド ライン コンパイラを使用してを使用して、アセンブリの参照に相当する、`/link`コンパイラ オプション。 クライアント プログラムは、これらのインターフェイスとして型指定されたランタイム オブジェクトのインスタンスを読み込むことができます。 厳密な名前のランタイム アセンブリの新しいバージョンを作成する場合、クライアント プログラムは、更新されたランタイム アセンブリを再コンパイルするのにはありません。 代わりに、クライアント プログラムは、どちらのバージョンのランタイム アセンブリは、パブリック インターフェイスの場合、埋め込み型情報を使用して、使用可能なを使用し続けます。  
  
 型の埋め込みの主な機能は、COM 相互運用機能アセンブリから型情報の埋め込みをサポートするためにはであるために完全に管理されたソリューションの種類の情報を埋め込む場合に次の制限が適用されます。  
  
-   COM 相互運用機能に固有の属性のみが埋め込まれます。その他の属性は無視されます。  
  
-   型がジェネリック パラメーターを使用してジェネリック パラメーターの型は、埋め込みの型には、その型がアセンブリの境界を越えて使用できません。 アセンブリの境界を越えるの例としては、別のアセンブリからメソッドの呼び出しをまたは型の派生型から別のアセンブリで定義されています。  
  
-   定数は埋め込まれません。  
  
-   <xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>クラスは、キーとして埋め込み型をサポートしていません</xref:System.Collections.Generic.Dictionary%602?displayProperty=fullName>。 キーとして埋め込み型をサポートするために、独自のディクショナリ型を実装することができます。  
  
 このチュートリアルでは、次の操作を行います。  
  
-   埋め込むことができる型情報を格納するパブリック インターフェイスを持つ厳密な名前のアセンブリを作成します。  
  
-   パブリック インターフェイスを実装する厳密な名前のランタイム アセンブリを作成します。  
  
-   パブリック インターフェイスから型情報を埋め込むし、ランタイム アセンブリからクラスのインスタンスを作成するクライアント プログラムを作成します。  
  
-   変更し、ランタイム アセンブリを再構築します。  
  
-   クライアント プログラムを再コンパイルしなくても新しいバージョンのランタイム アセンブリが使用されていることをクライアントのプログラムを実行します。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
## <a name="creating-an-interface"></a>インターフェイスを作成します。  
  
#### <a name="to-create-the-type-equivalence-interface-project"></a>型の等価性インターフェイス プロジェクトを作成するには  
  
1.  Visual Studio での**ファイル** メニューをポイント**新規** をクリックし、**プロジェクト**します。  
  
2.  **新しいプロジェクト**ダイアログ ボックスで、**プロジェクトの種類** ウィンドウで、ことを確認して**Windows**が選択されています。 選択**クラス ライブラリ**で、**テンプレート**ウィンドウです。 **名**ボックスに、入力`TypeEquivalenceInterface`、 をクリックし、 **OK**します。 新しいプロジェクトが作成されます。  
  
3.  **ソリューション エクスプ ローラー**Class1.vb ファイルを右クリックし、クリックして、**の名前を変更**します。 ファイルを`ISampleInterface.vb`ENTER キーを押します。 ファイルの名前変更の名前も変更は、クラスに`ISampleInterface`します。 このクラスは、クラスのパブリック インターフェイスを表します。  
  
4.  TypeEquivalenceInterface プロジェクトを右クリックし、クリックして**プロパティ**します。 **[コンパイル]** タブをクリックします。 など、開発用コンピューター上の有効な場所に出力パスを設定`C:\TypeEquivalenceSample`します。 この場所は、このチュートリアルの後の手順でも使用されます。  
  
5.  クリックしても、プロジェクトのプロパティを編集している間、**署名** タブをクリックします。 選択、**アセンブリに署名**オプション。 **厳密な名前キー ファイルを選択して**一覧で、クリックして** <New...> **</New...> 。 **キー ファイル名**ボックスに、入力`key.snk`します。 クリア、**パスワードでキー ファイルを保護する**チェック ボックスをオンします。 **[OK]** をクリックします。  
  
6.  ISampleInterface.vb ファイルを開きます。 ISampleInterface インターフェイスを作成する ISampleInterface クラス ファイルに次のコードを追加します。  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
7.  **ツール** メニューのをクリックして**Guid の作成**します。 **GUID の作成**ダイアログ ボックスで、をクリックして**レジストリ形式** をクリックし、**コピー**します。 [ **終了**] をクリックします。  
  
8.  `Guid`属性、サンプルの GUID を削除しからコピーした GUID を貼り付けます、 **GUID の作成** ダイアログ ボックス。 コピーした GUID には、中かっこ ({}) を削除します。  
  
9. **プロジェクト**] メニューのをクリックして**[すべてのファイル**します。  
  
10. **ソリューション エクスプ ローラー**、展開、 **My Project**フォルダーです。 AssemblyInfo.vb をダブルクリックします。 ファイルに次の属性を追加します。  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
     ファイルを保存します。  
  
11. プロジェクトを保存します。  
  
12. TypeEquivalenceInterface プロジェクトを右クリックし、クリックして**ビルド**します。 クラス ライブラリの .dll ファイルがコンパイルされ、指定したビルドの出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。  
  
## <a name="creating-a-runtime-class"></a>ランタイム クラスの作成  
  
#### <a name="to-create-the-type-equivalence-runtime-project"></a>型の等価性のランタイム プロジェクトを作成するには  
  
1.  Visual Studio での**ファイル** メニューをポイント**新規** をクリックし、**プロジェクト**します。  
  
2.  **新しいプロジェクト**ダイアログ ボックスで、**プロジェクトの種類** ウィンドウで、ことを確認して**Windows**が選択されています。 選択**クラス ライブラリ**で、**テンプレート**ウィンドウです。 **名**ボックスに、入力`TypeEquivalenceRuntime`、 をクリックし、 **OK**します。 新しいプロジェクトが作成されます。  
  
3.  **ソリューション エクスプ ローラー**Class1.vb ファイルを右クリックし、クリックして、**の名前を変更**します。 ファイルを`SampleClass.vb`ENTER キーを押します。 クラスの名前を変更も、ファイルの名前を変更する`SampleClass`です。 このクラスは実装、`ISampleInterface`インターフェイスです。  
  
4.  TypeEquivalenceRuntime プロジェクトを右クリックし、クリックして**プロパティ**します。 **[コンパイル]** タブをクリックします。 たとえば、TypeEquivalenceInterface プロジェクトで使用した同じ場所に出力パスを設定`C:\TypeEquivalenceSample`します。  
  
5.  クリックしても、プロジェクトのプロパティを編集している間、**署名** タブをクリックします。 選択、**アセンブリに署名**オプション。 **厳密な名前キー ファイルを選択して**一覧で、クリックして** <New...> **</New...> 。 **キー ファイル名**ボックスに、入力`key.snk`します。 クリア、**パスワードでキー ファイルを保護する**チェック ボックスをオンします。 **[OK]** をクリックします。  
  
6.  TypeEquivalenceRuntime プロジェクトを右クリックし、クリックして**参照の追加**します。 クリックして、**参照**タブし、出力パスのフォルダーを参照します。 TypeEquivalenceInterface.dll ファイルを選択し、クリックして**OK**します。  
  
7.  **プロジェクト**] メニューのをクリックして**[すべてのファイル**します。  
  
8.  **ソリューション エクスプ ローラー**、展開、**参照**フォルダーです。 TypeEquivalenceInterface 参照を選択します。 TypeEquivalenceInterface 参照の [プロパティ] ウィンドウで、設定、**特定のバージョン**プロパティを**False**します。  
  
9. SampleClass クラスを作成する SampleClass クラス ファイルに次のコードを追加します。  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
10. プロジェクトを保存します。  
  
11. TypeEquivalenceRuntime プロジェクトを右クリックし、クリックして**ビルド**します。 クラス ライブラリの .dll ファイルがコンパイルされ、指定したビルドの出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。  
  
## <a name="creating-a-client-project"></a>クライアント プロジェクトの作成  
  
#### <a name="to-create-the-type-equivalence-client-project"></a>型の等価性のクライアント プロジェクトを作成するには  
  
1.  Visual Studio での**ファイル** メニューをポイント**新規** をクリックし、**プロジェクト**します。  
  
2.  **新しいプロジェクト**ダイアログ ボックスで、**プロジェクトの種類** ウィンドウで、ことを確認して**Windows**が選択されています。 選択**コンソール アプリケーション**で、**テンプレート**ウィンドウです。 **名**ボックスに、入力`TypeEquivalenceClient`、 をクリックし、 **OK**します。 新しいプロジェクトが作成されます。  
  
3.  TypeEquivalenceClient プロジェクトを右クリックし、クリックして**プロパティ**します。 **[コンパイル]** タブをクリックします。 たとえば、TypeEquivalenceInterface プロジェクトで使用した同じ場所に出力パスを設定`C:\TypeEquivalenceSample`します。  
  
4.  TypeEquivalenceClient プロジェクトを右クリックし、クリックして**参照の追加**します。 クリックして、**参照**タブし、出力パスのフォルダーを参照します。 TypeEquivalenceInterface.dll ファイル (TypeEquivalenceRuntime.dll ではない) を選択し、クリックして**OK**します。  
  
5.  **プロジェクト**] メニューのをクリックして**[すべてのファイル**します。  
  
6.  **ソリューション エクスプ ローラー**、展開、**参照**フォルダーです。 TypeEquivalenceInterface 参照を選択します。 TypeEquivalenceInterface 参照の [プロパティ] ウィンドウで、設定、 **Embed Interop Types**プロパティを**True**します。  
  
7.  Module1.vb ファイルをクライアント プログラムを作成するには、次のコードを追加します。  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
8.  ビルドして、プログラムを実行するには、CTRL + F5 キーを押します。  
  
## <a name="modifying-the-interface"></a>インターフェイスを変更します。  
  
#### <a name="to-modify-the-interface"></a>インターフェイスを変更するには  
  
1.  Visual Studio での**ファイル** メニューをポイント**開く**、順にクリック**プロジェクト/ソリューション**します。  
  
2.  **プロジェクトを開く**ダイアログ ボックスで、TypeEquivalenceInterface プロジェクトを右クリックし、をクリックして**プロパティ**します。 **[アプリケーション]** タブをクリックします。 クリックして、**アセンブリ情報** ボタンをクリックします。 変更、**アセンブリ バージョン**と**ファイル バージョン**値`2.0.0.0`です。  
  
3.  ISampleInterface.vb ファイルを開きます。 ISampleInterface インターフェイスには、次のコード行を追加します。  
  
<CodeContentPlaceHolder>4</CodeContentPlaceHolder>  
     ファイルを保存します。  
  
4.  プロジェクトを保存します。  
  
5.  TypeEquivalenceInterface プロジェクトを右クリックし、クリックして**ビルド**します。 クラス ライブラリの .dll ファイルの新しいバージョンがコンパイルされ、指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。  
  
## <a name="modifying-the-runtime-class"></a>ランタイム クラスの変更  
  
#### <a name="to-modify-the-runtime-class"></a>ランタイム クラスを変更するには  
  
1.  Visual Studio での**ファイル** メニューをポイント**開く**、順にクリック**プロジェクト/ソリューション**します。  
  
2.  **プロジェクトを開く** ダイアログ ボックスで、TypeEquivalenceRuntime プロジェクトを右クリックし、クリックして**プロパティ**します。 **[アプリケーション]** タブをクリックします。 クリックして、**アセンブリ情報** ボタンをクリックします。 変更、**アセンブリ バージョン**と**ファイル バージョン**値`2.0.0.0`です。  
  
3.  SampleClass.vbfile を開きます。 SampleClass クラスに次のコード行を追加します。  
  
```vb  
Public Function GetDate() As DateTime Implements ISampleInterface.GetDate  
    Return Now  
End Function  
```  
  
     Save the file.  
  
4.  プロジェクトを保存します。  
  
5.  TypeEquivalenceRuntime プロジェクトを右クリックし、クリックして**ビルド**します。 クラス ライブラリの .dll ファイルの更新バージョンがコンパイルされ、以前に指定したビルド出力パス (たとえば、C:\TypeEquivalenceSample) に保存されます。  
  
6.  ファイル エクスプ ローラーでは、出力パスのフォルダー (たとえば、C:\TypeEquivalenceSample) を開きます。 プログラムを実行する TypeEquivalenceClient.exe をダブルクリックします。 プログラムは、再コンパイルされたことがなく TypeEquivalenceRuntime アセンブリの新しいバージョンに反映されます。  
  
## <a name="see-also"></a>関連項目  
 [/link (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/link.md)   
 [プログラミングの概念](../../../../visual-basic/programming-guide/concepts/index.md)   
 [アセンブリを使用したプログラミング](http://msdn.microsoft.com/library/25918b15-701d-42c7-95fc-c290d08648d6)   
 [アセンブリとグローバル アセンブリ キャッシュ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)

