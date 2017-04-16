---
title: "デスクトップ アプリケーションに対するサテライト アセンブリの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "配置 (アプリケーションを) [.NET Framework]、リソース"
  - "リソース ファイル、配置"
  - "ハブ アンド スポーク リソース配置モデル"
  - "リソース ファイル、パッケージ化"
  - "アプリケーション リソース、パッケージ化"
  - "公開キー、取得"
  - "サテライト アセンブリ"
  - "アセンブリ [.NET Framework]、署名"
  - "アプリケーション リソース、配置"
  - "Al.exe"
  - "GAC (グローバル アセンブリ キャッシュ)、サテライト アセンブリ"
  - "アセンブリ リンカー"
  - "ディレクトリの位置 (サテライト アセンブリ用の)"
  - "グローバル アセンブリ キャッシュ、サテライト アセンブリ"
  - "パッケージ化 (アプリケーション リソースの)"
  - "コンパイル (サテライト アセンブリの)"
  - "再署名 (アセンブリへの)"
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# デスクトップ アプリケーションに対するサテライト アセンブリの作成
リソース ファイルはローカライズされたアプリケーションの中心的な役割を果たします。  これは、通常、ユーザーがそれぞれの使用言語とカルチャの表示文字列、イメージ、およびそのほかのデータにユーザー固有の言語またはカルチャ用のリソースが使用できない場合、アプリケーションを、代替データを提供できるようになります。  .NET Framework には、ローカライズされたリソースを探し、取得するために、ハブ アンド スポーク モデルを使用します。  ハブはニュートラルまたは既定のカルチャと呼ばれる、単一カルチャ用のローカライズできない実行可能コードを含むメイン アセンブリです。  既定のカルチャは、アプリケーションで使用されるフォールバック カルチャです; これは、ローカライズされたリソースが使用できない場合に使用されます。  アプリケーションの既定のカルチャにカルチャを指定するために <xref:System.Resources.NeutralResourcesLanguageAttribute> 属性を使用します。  各スポークは、単一のローカライズされたカルチャ用のリソースを含むが、接続してコードを含まないサテライト アセンブリに。  サテライト アセンブリはメイン アセンブリの一部には含まれないため、簡単に特定のカルチャにアプリケーションのメイン アセンブリを交換しなくても、に対応するリソースだけを更新するか、または置換できます。  
  
> [!NOTE]
>  アプリケーションの既定のカルチャのリソースは、サテライト アセンブリに格納できます。  これを行うには、<xref:System.Resources.NeutralResourcesLanguageAttribute> 属性に <xref:System.Resources.UltimateResourceFallbackLocation?displayProperty=fullName>の値を割り当てます。  
  
## サテライト アセンブリの名前と場所  
 ハブ アンド スポーク モデルは、簡単に見つけて使用できるように、リソースを特定の場所に配置する必要があります。  、名前のリソースが正常にコンパイルするか、適切な場所に配置する場合、共通言語ランタイムはリソースを検出し、既定のカルチャのリソースを使用します。  <xref:System.Resources.ResourceManager> オブジェクトによって表される .NET Framework リソース マネージャーに自動的にローカライズされたリソースにアクセスするために使用されます。  リソース マネージャーは、次の項目が必要です。T:  
  
-   一つのサテライト アセンブリが特定のカルチャ用のリソースを含める必要があります。  つまり、複数の .txt をコンパイルする必要があります。また、単一のバイナリ .resources への .resx ファイルします。  
  
-   それぞれのローカライズされたカルチャ用のアプリケーション ディレクトリに個別のサブディレクトリが必要で、そのカルチャのリソースを格納します。  サブディレクトリ名は、カルチャ名と同じである必要があります。  また、グローバル アセンブリ キャッシュにサテライト アセンブリを格納できます。  この場合、アセンブリの厳密な名前のカルチャ情報のコンポーネントには、カルチャを指定する必要があります。このトピックで [グローバル アセンブリ キャッシュにサテライト アセンブリをインストールできます。](#SN) セクション"を参照してください\)。  
  
    > [!NOTE]
    >  アプリケーションにサブカルチャ用のリソースを含める場合は、アプリケーション ディレクトリに固有のサブディレクトリに各サブカルチャを配置します。  メイン カルチャのディレクトリのサブディレクトリにサブカルチャを入れないでください。  
  
-   サテライト アセンブリは、アプリケーションと同じ名前を持つファイル名拡張子「.resources.dll」を使用する必要があります。  たとえば、アプリケーションが Example.exe の場合、各サテライト アセンブリの名前は Example.resources.dll 必要があります。  サテライト アセンブリの名前は、リソース ファイルのカルチャがないことに注意してください。  ただし、サテライト アセンブリがカルチャを指定するディレクトリに表示されます。  
  
-   サテライト アセンブリのカルチャに関する情報は、アセンブリのメタデータに含まれている必要があります。  サテライト アセンブリ内のリソースを埋め込むために [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用する場合、サテライト アセンブリのメタデータにカルチャ名を保存するには、`/culture` オプションを指定します。  
  
 [グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)内にインストールしないアプリケーションについて、サンプルのディレクトリ構造と位置に関する要件を次の図に示します。  .txt および .resources 拡張の項目は、最終的なアプリケーションには付属していません。  それらは、最終的なサテライト リソース アセンブリを作成するまでの中間リソース ファイルです。  この例では、.txt ファイルを .resx ファイルに置き換えることもできます。  詳細については、「[" Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)」を参照してください。  
  
 ![サテライト アセンブリ](../../../docs/framework/resources/media/satelliteassemblydir.gif "satelliteassemblydir")  
サテライト アセンブリ ディレクトリ  
  
## サテライト アセンブリのコンパイル  
 バイナリ .resources ファイルにリソースを含む XML ファイル \(.resx\) または、テキスト ファイルをコンパイルするために [リソース ファイル ジェネレーター \(Resgen.exe\)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) を使用します。  その後、サテライト アセンブリに .resources ファイルをコンパイルするために [アセンブリ リンカー \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用します。  Al.exe は、指定された .resources ファイルからアセンブリを作成します。  サテライト アセンブリにはリソースのみを含めることができます。; 管理者として実行可能コードを含めることはできません。  
  
 次のコマンドは、Al.exe ドイツ語のリソース ファイル strings.de.resources からアプリケーション `Example` 用のサテライト アセンブリを作成します。  
  
```  
al /target:lib /embed:strings.de.resources /culture:de /out:Example.resources.dll  
```  
  
 次のコマンドは、Al.exe ファイル strings.de.resources からアプリケーション `Example` 用のサテライト アセンブリを作成します。  **\/template** オプションは、サテライト アセンブリは親アセンブリ \(Example.dll\) のカルチャ情報を除き、すべてのアセンブリ メタデータを継承します。  
  
```  
al /target:lib /embed:strings.de.resources /culture:de /out:Example.resources.dll /template:Example.dll  
```  
  
 次の表は、これらのコマンドで使用した Al.exe のオプションを示します。  
  
|オプション|説明|  
|-----------|--------|  
|**\/target:**ライブラリ|サテライト アセンブリがライブラリ \(.dll\) ファイルとしてコンパイルすることを指定します。  サテライト アセンブリが実行可能コードを含まず、アプリケーションのメイン アセンブリではないため、サテライト アセンブリは DLL として保存する必要があります。|  
|**\/embed:**strings.de.resources|リソース ファイルの名前を、Al.exe がアセンブリをコンパイルするときに埋め込むに指定します。  サテライト アセンブリに複数の .resources ファイルを埋め込むことができます。ハブ アンド スポーク モデルに従う場合は、カルチャごとに、1 個のサテライト アセンブリをコンパイルする必要があります。  ただし、文字列、オブジェクトの別の .resources ファイルを作成できます。|  
|**\/culture:**de|リソースのカルチャをコンパイルするように指定します。  共通言語ランタイムは、指定されたカルチャ用のリソースを検索するときに、この情報を使用します。  このオプションを省略すると、Al.exe はリソースがコンパイルされ、ランタイムはそのリソースを検出できなくユーザーが要求した場合。|  
|**\/out:**Example.resources.dll|出力ファイルの名前を指定します。  名前は名前付け標準 *baseName*.resources に従う必要があります。*baseName* はメイン アセンブリと *extension* の名前の*extension*は、有効なファイル名拡張子 \(.dll\) です。  ランタイムは、出力ファイル名からサテライト アセンブリのカルチャを判断することはできません。; これを指定するために **\/culture** オプションを使用する必要があります。|  
|**\/template:**Example.dll|サテライト アセンブリのカルチャ フィールドを除く、すべてのアセンブリ メタデータを継承するアセンブリを指定します。  このオプションは [厳密な名前](../../../docs/framework/app-domains/strong-named-assemblies.md)が指定されたアセンブリを指定している場合にのみサテライト アセンブリに影響します。|  
  
 有効な Al.exe のオプションの一覧については [アセンブリ リンカー \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md)を参照してください。  
  
## サテライト アセンブリ: 例  
 次にローカライズされたメッセージを含むメッセージ ボックスを表示する「Hello world」の簡単な例です。  例では、英語 \(米国\)、フランス語 \(フランス\)、ロシア語 \(ロシア語\) のカルチャのリソースが含まれ、フォールバック カルチャは英語です。  例を作成するには、次の手順を実行します。:  
  
1.  Create a resource ファイルは既定のカルチャ用のリソースを含めるに Greeting.resx または Greeting.txt を指定します。  値が「Hello world\!」という `HelloString` という名前の一つの文字列を格納します。このファイル。  
  
2.  English \(en\) がアプリケーションの既定のカルチャであることを示すには、アプリケーションの AssemblyInfo ファイルまたはアプリケーションのメイン アセンブリにコンパイルされる主要なソース ファイルに <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> の次の属性を追加します。  
  
     [!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
     [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3.  次のようにアプリケーションに新しいカルチャ \(en\-US、fr\-FR と ru RU\) のサポートを追加する:  
  
    -   英語 \(米国\) en\-US または English カルチャを、Greeting.en\-US.resx または Greeting.en\-US.txt をサポートするには、ストアを作成するための指定されたリソース ファイルは、一つの文字列値が「Hello World\!」が `HelloString` という名前です。  
  
    -   \(フランス語\) fr\-FR またはフランスのカルチャを、Greeting.fr\-FR.resx または Greeting.fr\-FR.txt をサポートするには、ストアを作成するための指定されたリソース ファイルは、一つの文字列は、値が「Salut ダフ屋 le Monde が\!」であるという `HelloString`  
  
    -   ru RU またはロシア語個 \(ロシア語\) カルチャを、Greeting.ru\-RU.resx または Greeting.ru\-RU.txt をサポートするには、ストアを作成するための指定されたリソース ファイルは、一つの文字列は、値が「Всем привет\!」が `HelloString` という名前です。  
  
4.  バイナリ .resources ファイルに各テキストまたは XML リソース ファイルをコンパイルするために [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) を使用します。  出力は、.resx ファイルまたは .txt ファイルと同じルート ファイル名を持つ、拡張子 .resources ファイル セットです。  Visual Studio と例を作成すると、コンパイル処理は自動的に処理されます。  Visual Studio を使用していない場合は、.resx ファイルを .resources ファイルにコンパイルするには、次のコマンドを実行する:  
  
    ```  
  
    resgen Greeting.resx  
    resgen Greeting.en-us.resx  
    resgen Greeting.fr-FR.resx  
    resgen Greeting.ru-RU.resx  
  
    ```  
  
     リソースが XML ファイルではなく、テキスト ファイルの場合は、.txt と .resx 拡張子を置き換えます。  
  
5.  アプリケーションのメイン アセンブリに既定のカルチャのリソース ファイルとともに次のソース・コードをコンパイルする:  
  
    > [!IMPORTANT]
    >  例を作成したときに、Visual Studio ではなく、コマンド ラインを使用すると、次に <xref:System.Resources.ResourceManager> クラス コンストラクターの呼び出しを変更する必要があります: `ResourceManager rm = new ResourceManager("Greetings",``typeof(Example).Assembly);`  
  
     [!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
     [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]  
  
     アプリケーションが Example という名前で、コマンド ラインからコンパイルする場合、C\# コンパイラのコマンドは、次の操作:  
  
    ```  
    csc Example.cs /res:Greeting.resources  
    ```  
  
     Visual Basic の対応するコンパイラのコマンドは、次の操作:  
  
    ```  
    vbc Example.vb /res:Greeting.resources  
    ```  
  
6.  アプリケーションでサポートされているそれぞれのローカライズされたカルチャのメイン アプリケーション ディレクトリのサブディレクトリを作成します。  en\-US、fr\-FR と ru RU サブディレクトリを作成する必要があります。  Visual Studio は、コンパイル処理の一部としてこれらのサブディレクトリを自動的に作成されます。  
  
7.  各カルチャ固有の .resources ファイルをサテライト アセンブリに埋め込み、適切なディレクトリに保存します。  各 .resources ファイルの要素を指定するコマンドを次に示します。:  
  
    ```  
    al /target:lib /embed:Greeting.culture.resources /culture:culture /out:culture\Example.resources.dll  
    ```  
  
     *culture* がリソースをサテライト アセンブリに含まれるカルチャの名前です。  Visual Studio は、この処理を自動的に処理します。  
  
 この例を実行できます。  これはランダムにサポートされているカルチャの 1 に現在のカルチャを、ローカライズされたメッセージを表示します。  
  
<a name="SN"></a>   
## グローバル アセンブリ キャッシュにサテライト アセンブリをインストールできます。  
 ローカル アプリケーション サブディレクトリにアセンブリをインストールする代わりに、グローバル アセンブリ キャッシュにインストールできます。  これは、複数のアプリケーションで使用されるクラス ライブラリのリソース アセンブリとクラス ライブラリがある場合に特に便利です。  
  
 アセンブリをグローバル アセンブリ キャッシュにインストールするには、アセンブリに厳密な名前が必要です。  厳密な名前を持つアセンブリには、有効な公開\/秘密キーのペアによる署名が付いています。  これらは、バインド要求を満たすために使用するアセンブリ バージョンを決定するためにランタイムが使用するバージョン情報が含まれています。  厳密な名前とバージョン管理の詳細については、「[Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md)」を参照してください。  厳密な名前の詳細については、「[Strong\-Named Assemblies](../../../docs/framework/app-domains/strong-named-assemblies.md)」を参照してください。  
  
 通常、アプリケーションの開発中に、最終的な公開\/秘密キーのペアにアクセスすることはありません。  サテライト アセンブリをグローバル アセンブリ キャッシュ内にインストールし、そのアセンブリが確実に予測どおりに機能するようにするために、遅延署名と呼ばれる技術を使用できます。  厳密な名前の署名のためにアセンブリに遅延署名ビルド時のアセンブリ、ファイル内の領域を確保します。  実際の署名は後で、最終的な公開\/秘密キーのペアを使用できる場合、遅延します。  遅延署名に関する詳細については、「[アセンブリへの遅延署名](../../../docs/framework/app-domains/delay-sign-assembly.md)」を参照してください。  
  
### 公開キーの取得  
 アセンブリへの署名を遅延するには、公開キーにアクセスする必要があります。  [Strong Name Tool \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)の使用、または最終的な署名を行う、または公開キーを作成します。できます企業の組織の実際の公開キーを取得します。  
  
 次のコマンドは、Sn.exe テスト用の公開キーと秘密キーのペアを生成します。  **–k** オプションは、Sn.exe で新しいキー ペアを作成し、TestKeyPair.snk というファイルに格納するように指定します。  
  
```  
sn –k TestKeyPair.snk   
```  
  
 テスト用のキー ペアを含むファイルから公開キーを抽出できます。  次のコマンドは、TestKeyPair.snk から公開キーを抽出し、PublicKey.snk に保存する:  
  
```  
sn –p TestKeyPair.snk PublicKey.snk  
```  
  
### アセンブリへの遅延署名  
 公開キーを取得または作成したら、アセンブリをコンパイルし、遅延署名を指定するために [アセンブリ リンカー \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用します。  
  
 次のコマンドは、Al.exe strings.ja.resources ファイルからアプリケーション StringLibrary の強名前付きなサテライト アセンブリを作成する:  
  
```  
al /target:lib /embed:strings.ja.resources /culture:ja /out:StringLibrary.resources.dll /delay+ /keyfile:PublicKey.snk  
```  
  
 **\/delay\+** オプションは、アセンブリへの署名とアセンブリ \(Assembly Linker ことを指定します。  **\/keyfile** オプションは、アセンブリへの署名を遅延するために使用する公開キーを含むキー ファイルの名前を指定します。  
  
### アセンブリへの再署名  
 アプリケーションを配置する前に、実際のキー ペアで遅延署名されたサテライト アセンブリを再署名する必要があります。  Sn.exe を使用して行うことができます。  
  
 次のコマンドは、Sn.exe ファイル RealKeyPair.snk に格納されているキーのペアで StringLibrary.resources.dll に署名します。  **–R** オプションは、以前に符号付きなまたはの遅延署名されたアセンブリを再署名する必要があることを指定します。  
  
```  
sn –R StringLibrary.resources.dll RealKeyPair.snk   
```  
  
### グローバル アセンブリ キャッシュへのサテライト アセンブリのインストール  
 ランタイムがリソース フォールバック プロセスによってリソースを検索するときには、[グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md) を最初になります。\(詳細については、[リソースのパッケージ化と配置](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) 「の"リソース フォールバック プロセス」を参照します。サテライト アセンブリが厳密な名前で署名すると、グローバル アセンブリ キャッシュに [Global Assembly Cache Tool \(Gacutil.exe\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)を使用してインストールできます。  
  
 次のコマンドは、Gacutil.exe はグローバル アセンブリ キャッシュに StringLibrary.resources.dll をインストールする:  
  
```  
gacutil /i:StringLibrary.resources.dll  
```  
  
 **\/i** オプションは、Gacutil.exe をグローバル アセンブリ キャッシュに指定されたアセンブリをインストールする必要があることを指定します。  サテライト アセンブリのキャッシュにインストールされた後で、サテライト アセンブリを使用するようにデザインされたすべてのアプリケーションで使用できるようになった含むリソース。  
  
### グローバル アセンブリ キャッシュのリソース: 例  
 次の例は、.NET Framework クラス ライブラリでリソース ファイルからローカライズされたメッセージを取得して返すためにメソッドを使用します。  ライブラリやリソースをグローバル アセンブリ キャッシュに登録されます。  例では、英語 \(米国\)、フランス語 \(フランス\)、ロシア語 \(ロシア語\)、および English カルチャのリソースが含まれています。  英語では既定のカルチャです。; このリソースは、メイン アセンブリに格納されます。  最初の例では、アセンブリに遅延署名が公開キーと秘密キーのペアの公開キーを使用してライブラリとサテライト アセンブリし、それらに再署名します。  例を作成するには、次の手順を実行します。:  
  
1.  Visual Studio を使用して、公開キーという名前の ResKey.snk 秘密キーのペアを作成する [Strong Name Tool \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) 次のコマンドを使用します。:  
  
    ```  
    sn –k ResKey.snk  
    ```  
  
     Visual Studio を使用している場合は、キー ファイルを生成するには、プロジェクトの **\[プロパティ\]** ダイアログ ボックスの **\[署名\]** タブを使用します。  
  
2.  PublicKey.snk という名前の公開キー ファイルを作成する [Strong Name Tool \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) 次のコマンドを使用します。:  
  
    ```  
    sn –p ResKey.snk PublicKey.snk  
    ```  
  
3.  Create a resource ファイルは既定のカルチャ用のリソースを含めるに Strings.resx という名前です。  か」のように、値を持つ `Greeting` という名前の一つの文字列を格納します。そのファイル。  
  
4.  「en」がアプリケーションの既定のカルチャであることを示すには、アプリケーションの AssemblyInfo ファイルまたはアプリケーションのメイン アセンブリにコンパイルされる主要なソース ファイルに <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> の次の属性を追加する:  
  
     [!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
     [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]  
  
5.  次のようにアプリケーションに新しいカルチャ \(en\-US、fr\-FR カルチャと ru RU\) のサポートを追加する:  
  
    -   「en\-US」、つまり英語 \(米国\) カルチャを、Strings.en\-US.resx または Strings.en\-US.txt をサポートするには、ストアを作成するための指定されたリソース ファイルは、一つの文字列は、値が「Hello\!」を持つ `Greeting` という名前です。  
  
    -   「fr\-FR」、つまりフランス語 \(フランス\) のカルチャをサポートするには、Strings.fr\-FR.resx または Strings.fr\-FR.txt とストアという名前のリソース ファイルを作成するには、一つの文字列は、値が「糖菓 jour\!」が `Greeting` という名前です。  
  
    -   「ru\-RU」の各または \(ロシア語ロシア語\) のカルチャをサポートするには、Strings.ru\-RU.resx または Strings.ru\-RU.txt とストアという名前のリソース ファイルを作成するには、一つの文字列は、値が「Привет\!」が `Greeting` という名前です。  
  
6.  バイナリ .resources ファイルに各テキストまたは XML リソース ファイルをコンパイルするために [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) を使用します。  出力は、.resx ファイルまたは .txt ファイルと同じルート ファイル名を持つ、拡張子 .resources ファイル セットです。  Visual Studio と例を作成すると、コンパイル処理は自動的に処理されます。  Visual Studio を使用していない場合は、.resx ファイルを .resources ファイルにコンパイルするには、次のコマンドを実行する:  
  
    ```  
    resgen filename  
    ```  
  
     *filename* が .resx ファイルまたはテキスト ファイルの省略可能なパス、ファイル名と拡張子です。  
  
7.  遅延署名されたライブラリ アセンブリという StringLibrary.dll に既定のカルチャのリソース ファイルとともに StringLibrary.cs の次のソース・コードをコンパイルする:  
  
    > [!IMPORTANT]
    >  例を作成したときに、Visual Studio ではなく、コマンド ラインを使用して `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`に <xref:System.Resources.ResourceManager> クラス コンストラクターの呼び出しを変更する必要があります。  
  
     [!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
     [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]  
  
     C\# コンパイラのコマンドは、次の操作:  
  
    ```  
    csc /t:library /resource:Strings.resources /delaysign+ /keyfile:publickey.snk StringLibrary.cs  
    ```  
  
     Visual Basic の対応するコンパイラのコマンドは、次の操作:  
  
    ```  
    vbc /t:library /resource:Strings.resources /delaysign+ /keyfile:publickey.snk StringLibrary.vb  
    ```  
  
8.  アプリケーションでサポートされているそれぞれのローカライズされたカルチャのメイン アプリケーション ディレクトリのサブディレクトリを作成します。  en\-US、fr\-FR と ru RU サブディレクトリを作成する必要があります。  Visual Studio は、コンパイル処理の一部としてこれらのサブディレクトリを自動的に作成されます。  すべてのサテライト アセンブリが同じファイル名を持つため、個々のカルチャのサテライト アセンブリを格納するために、公開キーと秘密キーのキー ペアで署名するまでサブディレクトリが使用されます。  
  
9. 各カルチャ固有の .resources ファイルを遅延署名されたサテライト アセンブリに埋め込み、適切なディレクトリに保存します。  各 .resources ファイルの要素を指定するコマンドを次に示します。:  
  
    ```  
    al /target:lib /embed:Strings.culture.resources /culture:culture /out:culture\StringLibrary.resources.dll /delay+ /keyfile:publickey.snk  
    ```  
  
     *culture* がカルチャの名前です。  この例では、カルチャ名は en\-US、fr\-FR と ru RU です。  
  
10. [Strong Name Tool \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) を使用して StringLibrary.dll に再署名します。次のよう:  
  
    ```  
    sn –R StringLibrary.dll RealKeyPair.snk  
    ```  
  
11. 個々のサテライト アセンブリに再署名します。  次のように、各サテライト アセンブリでこれを行うには、[Strong Name Tool \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) を使用する:  
  
    ```  
    sn –R StringLibrary.resources.dll RealKeyPair.snk  
    ```  
  
12. 次のコマンドを使用して StringLibrary.dll、グローバル アセンブリ キャッシュのサテライト アセンブリに登録する:  
  
    ```  
    gacutil /i filename  
    ```  
  
     *filename* を登録するファイルの名前です。  
  
13. Visual Studio を使用している場合は、`Example`という名前の **\[コンソール アプリケーション\]** の新しいプロジェクトを作成し、StringLibrary.dll への参照、および次のソース・コードを追加し、コンパイルします。  
  
     [!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
     [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]  
  
     コマンド ラインからコンパイルするには、C\# コンパイラでは、次のコマンドを使用します。:  
  
    ```  
    csc Example.cs /r:StringLibrary.dll   
    ```  
  
     Visual Basic コンパイラのコマンド ラインでは、次の操作:  
  
    ```  
    vbc Example.vb /r:StringLibrary.dll   
    ```  
  
14. Example.exe を実行します。  
  
## 参照  
 [リソースのパッケージ化と配置](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)   
 [アセンブリへの遅延署名](../../../docs/framework/app-domains/delay-sign-assembly.md)   
 [Al.exe \(アセンブリ リンカー\)](../../../docs/framework/tools/al-exe-assembly-linker.md)   
 [Sn.exe \(厳密名ツール\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)   
 [Gacutil.exe \(グローバル アセンブリ キャッシュ ツール\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)   
 [デスクトップ アプリケーションのリソース](../../../docs/framework/resources/index.md)