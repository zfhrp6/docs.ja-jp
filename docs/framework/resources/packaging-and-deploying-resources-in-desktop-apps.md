---
title: "デスクトップ アプリケーションでのリソースのパッケージ化と配置"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- single resource assembly
- satellite assemblies
- default culture for applications
- names [.NET Framework], resources
- fallback process for resources
- grouping cultures
- application resources, deploying
- application resources, naming conventions
- culture, packaging and deploying resources
- resource files, naming conventions
- packaging application resources
- application resources, fallback processes
- resource files, fallback processes
- localizing resources
- neutral cultures
ms.assetid: b224d7c0-35f8-4e82-a705-dd76795e8d16
caps.latest.revision: 26
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5de456ff1a371a43241dba3b47be7dcd80bf8f70
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="packaging-and-deploying-resources-in-desktop-apps"></a>デスクトップ アプリケーションでのリソースのパッケージ化と配置
アプリケーションは、<xref:System.Resources.ResourceManager> クラスによって表される .NET Framework リソース マネージャーに依存して、ローカライズされたリソースを取得します。 リソース マネージャーでは、リソースのパッケージ化と配置にハブ アンド スポーク モデルを使うことが想定されています。 ハブは、ローカライズできない実行可能コードと、ニュートラル カルチャまたは既定のカルチャと呼ばれる単一カルチャ用のリソースを含む、メイン アセンブリです。 既定のカルチャはアプリケーション用のフォールバック カルチャです。つまり、ローカライズされたリソースが見つからない場合に使われるリソースのカルチャです。 各スポークは、単一のカルチャ用のリソースを含むがコードは含まないサテライト アセンブリに接続します。  
  
 このモデルにいくつかの利点があります。  
  
-   アプリケーションを配置した後で、段階的に新しいカルチャのリソースを追加できます。 カルチャに固有のリソースを後で開発するには多くの時間を必要とすることがあるため、後から追加できれば、メイン アプリケーションを最初にリリースしておき、カルチャ固有のリソースを後で配布できます。  
  
-   アプリケーションを再コンパイルすることなく、アプリケーションのサテライト アセンブリを更新および変更することができます。  
  
-   アプリケーションで読み込む必要があるのは、特定のカルチャに必要なリソースを含むサテライト アセンブリだけです。 このようにすると、システム リソースの使用を大幅に減らすことができます。  
  
 ただし、このモデルにも短所はあります。  
  
-   複数のリソース セットを管理する必要があります。  
  
-   複数の構成をテストする必要があるため、アプリケーションのテストの初期コストが増えます。 長期的に見れば、複数の各国語バージョンを並列にテストして管理するより、複数のサテライトを持つ 1 つの中核アプリケーションをテストする方が簡単かつ安価であることに注意してください。  
  
## <a name="resource-naming-conventions"></a>リソースの名前付け規則  
 アプリケーションのリソースをパッケージ化するときは、共通言語ランタイムで想定されているリソース名前付け規則を使って、リソースに名前を付ける必要があります。 ランタイムは、そのカルチャ名でリソースを識別します。 各カルチャには一意の名前が指定されています。通常は、言語に関連付けられた小文字 2 文字のカルチャ名と、必要に応じて、国または地域に関連付けられた大文字 2 文字のサブカルチャ名を組み合わせたものです。 カルチャ名の後にダッシュ (-) で区切ってサブカルチャ名は記述します。 日本で話される日本語は ja-JP、米国で話される英語は en-US、ドイツで話されるドイツ語は de-DE、オーストリアで話されるドイツ語は de-AT などとなります。 カルチャ名の詳細な一覧については、Go Global デベロッパー センターの「[National Language Support (NLS) API Reference](http://go.microsoft.com/fwlink/?LinkId=200048)」(各国語サポート (NLS) の API リファレンス) をご覧ください。  
  
> [!NOTE]
>  リソース ファイルの作成について詳しくは、MSDN ライブラリの「[リソース ファイルの作成](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)」および「[サテライト アセンブリの作成](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)」をご覧ください。  
  
<a name="cpconpackagingdeployingresourcesanchor1"></a>   
## <a name="the-resource-fallback-process"></a>リソース フォールバック プロセス  
 リソースのパッケージ化と配置のハブ アンド スポーク モデルでは、適切なリソースを見つけるためにフォールバック プロセスが使われます。 アプリケーションが使用できないローカライズされたリソースを要求した場合、共通言語ランタイムは、カルチャの階層で、ユーザーのアプリケーションの要求と最もよく一致する適切なフォールバック リソースを検索し、例外がスローされるのは最終的な手段としてのみです。 階層の各レベルで適切なリソースが見つかった場合、ランタイムはそれを使います。 リソースが見つからない場合、次のレベルで検索が続けられます。  
  
 検索のパフォーマンスを向上させるには、<xref:System.Resources.NeutralResourcesLanguageAttribute> 属性をメイン アセンブリに適用し、メイン アセンブリで動作するニュートラル言語の名前をそれに渡します。  
  
> [!TIP]
>  [\<relativeBindForResources>](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) 構成要素を使うことで、リソース フォールバック プロセスおよびランタイムがリソース アセンブリをプローブするプロセスを、最適化できる場合があります。 詳しくは、「[リソース フォールバック プロセスの最適化](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#Optimizing)」セクションをご覧ください。  
  
 リソース フォールバック プロセスには次の手順が含まれます。  
  
1.  ランタイムは最初に、[グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)で、アプリケーションに対して要求されたカルチャと一致するアセンブリを調べます。  
  
     グローバル アセンブリ キャッシュには、多くのアプリケーションで共有されるリソース アセンブリを格納できます。 これにより、作成するすべてのアプリケーションのディレクトリ構造に特定のリソース セットを含める必要がなくなります。 アセンブリへの参照が見つかると、ランタイムは要求されたリソースのアセンブリを検索します。 アセンブリでエントリが見つかると、ランタイムは要求されたリソースを使います。 エントリが見つからない場合は、検索を続けます。  
  
2.  次に、ランタイムは、現在実行中のアセンブリのディレクトリで、要求されたカルチャと一致するディレクトリを調べます。 ディレクトリが見つかった場合、要求されたカルチャの有効なサテライト アセンブリをそのディレクトリで検索します。 ランタイムはその後、要求されたリソースのサテライト アセンブリを検索します。 アセンブリでリソースが見つかると、それを使用します。 リソースが見つからない場合は、検索を続けます。  
  
3.  ランタイムは次に、Windows インストーラーに問い合わせて、サテライト アセンブリをオンデマンドでインストールする必要があるかどうかを確認します。 必要がある場合は、インストールを処理し、アセンブリを読み込んで要求されたリソースを検索します。 アセンブリでリソースが見つかると、それを使用します。 リソースが見つからない場合は、検索を続けます。  
  
4.  ランタイムは <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> イベントを生成し、サテライト アセンブリが見つからないことを示します。 イベントを処理することを選択した場合、イベント ハンドラーはリソースを検索に使用するサテライト アセンブリへの参照を返すことができます。 それ以外の場合、イベント ハンドラーは `null` を返し、検索が続けられます。  
  
5.  ランタイムは次に、再びグローバル アセンブリ キャッシュで、今度は要求されたカルチャの親アセンブリを検索します。 親アセンブリがグローバル アセンブリ キャッシュに存在する場合、ランタイムはそのアセンブリで要求されたリソースを検索します。  
  
     親カルチャは、適切なフォールバック カルチャとして定義されます。 例外をスローするよりは何らかのリソースを提供する方がよいので、親をフォールバック候補として考えます。 このプロセスでは、リソースを再利用することもできます。 子カルチャが要求されたリソースをローカライズする必要がない場合にのみ、親レベルで特定のリソースを含める必要があります。 たとえば、en (ニュートラル英語)、en-GB (英国で話される英語)、および en-US (米国で話される英語) のサテライト アセンブリを提供する場合、en サテライトで一般的な用語を提供し、en-GB および en-US サテライトでは異なる用語のみの上書きを提供できます。  
  
6.  次に、ランタイムは、現在実行中のアセンブリのディレクトリが親ディレクトリを含むかどうかを調べます。 親ディレクトリが存在する場合、ランタイムはそのディレクトリで、親カルチャの有効なサテライト アセンブリを検索します。 アセンブリが見つかると、ランタイムは要求されたリソースのアセンブリを検索します。 リソースが見つかった場合は、それを使用します。 リソースが見つからない場合は、検索を続けます。  
  
7.  ランタイムは次に、Windows インストーラーに問い合わせて、親サテライト アセンブリをオンデマンドでインストールする必要があるかどうかを確認します。 必要がある場合は、インストールを処理し、アセンブリを読み込んで要求されたリソースを検索します。 アセンブリでリソースが見つかると、それを使用します。 リソースが見つからない場合は、検索を続けます。  
  
8.  ランタイムは <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> イベントを生成し、適切なフォールバック リソースが見つからないことを示します。 イベントを処理することを選択した場合、イベント ハンドラーはリソースを検索に使用するサテライト アセンブリへの参照を返すことができます。 それ以外の場合、イベント ハンドラーは `null` を返し、検索が続けられます。  
  
9. ランタイムは次に、前の 3 つの手順と同じように、可能性のある多くのレベルで親アセンブリを検索します。 各カルチャの親は 1 つだけで、<xref:System.Globalization.CultureInfo.Parent%2A?displayProperty=fullName> プロパティによって定義されていますが、親がそれ自身の親を持つ可能性があります。 親カルチャの検索は、<xref:System.Globalization.CultureInfo.Parent%2A> プロパティが <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=fullName> を返した時点で停止します。リソース フォールバックでは、インバリアント カルチャは、親カルチャまたはリソースを持つことができるカルチャと見なされません。  
  
10. もともと指定されていたカルチャおよびすべての親を検索してもリソースが見つからない場合は、既定の (フォールバック) カルチャのリソースが使われます。 通常、既定のカルチャのリソースは、メイン アプリケーション アセンブリに格納されています。 ただし、<xref:System.Resources.NeutralResourcesLanguageAttribute> 属性の <xref:System.Resources.NeutralResourcesLanguageAttribute.Location%2A> プロパティに値 <xref:System.Resources.UltimateResourceFallbackLocation.Satellite> を指定することで、リソースの最終的なフォールバックの場所が、メイン アセンブリではなくサテライト アセンブリであることを示すことができます。  
  
    > [!NOTE]
    >  既定のリソースは、メイン アセンブリでコンパイルできる唯一のリソースです。 <xref:System.Resources.NeutralResourcesLanguageAttribute> 属性を使ってサテライト アセンブリを指定していない場合、最終的なフォールバック (最後の親) になります。 したがって、常に既定のリソース セットをメイン アセンブリに含めることをお勧めします。 これは、例外がスローされるのを防ぐのに役立ちます。 既定のリソース ファイルを含めることにより、すべてのリソースに対してフォールバックが提供され、固有のカルチャではなくても、常に少なくとも 1 つのリソースがユーザーに存在することが保証されます。  
  
11. 最後に、既定の (フォールバック) カルチャのリソースが見つからない場合は、<xref:System.Resources.MissingManifestResourceException> または <xref:System.Resources.MissingSatelliteAssemblyException> 例外がスローされて、リソースが見つからなかったことが示されます。  
  
 たとえば、アプリケーションがスペイン語 (メキシコ) (es-MX カルチャ) にローカライズされたリソースを要求しているものとします。 ランタイムは最初に、グローバル アセンブリ キャッシュで es-MX と一致するアセンブリを検索しますが、見つかりません。 ランタイムは、現在実行中のアセンブリのディレクトリで es-MX のディレクトリを検索します。 見つからない場合、ランタイムは再びグローバル アセンブリ キャッシュで、適切なフォールバック カルチャ (この場合は es (スペイン語)) を反映する親アセンブリを検索します。 親アセンブリが見つからない場合、ランタイムは、対応するリソースが見つかるまで、親アセンブリのすべての可能性のあるレベルで、es-MX カルチャを検索します。 それでもリソースが見つからない場合、ランタイムは、既定のカルチャのリソースを使います。  
  
<a name="Optimizing"></a>   
### <a name="optimizing-the-resource-fallback-process"></a>リソース フォールバック プロセスを最適化する  
 次の条件が満たされていれば、ランタイムがサテライト アセンブリでリソースを検索するプロセスを最適化することができます。  
  
-   サテライト アセンブリが、コード アセンブリと同じ場所に配置されていること。 コード アセンブリが[グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)にインストールされている場合、サテライト アセンブリもグローバル アセンブリ キャッシュにインストールされます。 コード アセンブリがディレクトリにインストールされている場合、サテライト アセンブリはそのディレクトリのカルチャ固有のフォルダーにインストールされます。  
  
-   サテライト アセンブリは、オンデマンドではインストールされません。  
  
-   アプリケーションのコードは、<xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> イベントを処理しません。  
  
 次の例に示すように、アプリケーション構成ファイルで [\<relativeBindForResources>](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) 要素を指定し、その `enabled` 属性を `true` に設定することにより、サテライト アセンブリのプローブを最適化します。  
  
```xml  
<configuration>  
   <runtime>  
      <relativeBindForResources enabled="true" />  
   </runtime>  
</configuration>  
```  
  
 サテライト アセンブリの最適化されたプローブは、オプトイン機能です。 つまり、アプリケーションの構成ファイルに `enabled` 属性が `true` に設定されている [\<relativeBindForResources>](../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md) 要素が存在しない限り、ランタイムは「[リソース フォールバック プロセス](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md#cpconpackagingdeployingresourcesanchor1)」で説明されている手順に従います。 その場合、サテライト アセンブリをプローブするプロセスは次のように変更されます。  
  
-   ランタイムは、親コード アセンブリの場所を使って、サテライト アセンブリをプローブします。 親アセンブリがグローバル アセンブリ キャッシュにインストールされている場合、ランタイムはアプリケーションのディレクトリではなくキャッシュ内をプローブします。 親アセンブリがアプリケーション ディレクトリにインストールされている場合、ランタイムはグローバル アセンブリ キャッシュではなくアプリケーション ディレクトリをプローブします。  
  
-   ランタイムは、Windows インストーラーでサテライト アセンブリのオンデマンド インストールを照会しません。  
  
-   特定のリソース アセンブリのプローブが失敗した場合、ランタイムは <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> イベントを生成しません。  
  
### <a name="ultimate-fallback-to-satellite-assembly"></a>サテライト アセンブリへの最終的なフォールバック  
 必要に応じて、メイン アセンブリからリソースを削除し、特定のカルチャに対応するサテライト アセンブリから最終的なフォールバック リソースを読み込む必要があることをランタイムに指定できます。 フォールバック プロセスを制御するには、<xref:System.Resources.NeutralResourcesLanguageAttribute.%23ctor%28System.String%2CSystem.Resources.UltimateResourceFallbackLocation%29?displayProperty=fullName> コンストラクターを使用し、リソース マネージャーがメイン アセンブリまたはサテライト アセンブリからフォールバック リソースを抽出する必要があるかどうかを指定する <xref:System.Resources.UltimateResourceFallbackLocation> パラメーターの値を指定します。  
  
 次の例では、<xref:System.Resources.NeutralResourcesLanguageAttribute> 属性を使って、フランス語 (fr) のサテライト アセンブリにアプリケーションのフォールバック リソースを格納しています。  この例には、`Greeting` という名前の 1 つの文字列リソースを定義するテキスト ベースのリソース ファイルが 2 つあります。 1 番目の resources.fr.txt には、フランス語の言語リソースが含まれています。  
  
```  
Greeting=Bon jour!  
```  
  
 2 番目の resources,ru.txt には、ロシア語の言語リソースが含まれています。  
  
```  
Greeting=Добрый день  
```  
  
 コマンド ラインから[リソース ファイル ジェネレーター (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) を実行することで、これら 2 つのファイルを .resources にコンパイルします。  フランス語リソースの場合、コマンドは次のようになります。  
  
 **resgen.exe resources.fr.txt**  
  
 ロシア語リソースの場合、コマンドは次のようになります。  
  
 **resgen.exe resources.ru.txt**  
  
 コマンド ラインから[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) を実行することにより、.resources ファイルをダイナミック リンク ライブラリに埋め込みます。フランス語リソースの場合のコマンドは次のとおりです。  
  
 **al /t:lib /embed:resources.fr.resources /culture:fr /out:fr\Example1.resources.dll**  
  
 ロシア語リソースの場合のコマンドは次のとおりです。  
  
 **al /t:lib /embed:resources.ru.resources /culture:ru /out:ru\Example1.resources.dll**  
  
 アプリケーションのソース コードは、Example1.cs または Example1.vb という名前のファイルに存在します。 このファイルには、既定のアプリケーション リソースが fr サブディレクトリにあることを示す <xref:System.Resources.NeutralResourcesLanguageAttribute> 属性が含まれます。 リソース マネージャーをインスタンス化し、`Greeting` リソースの値を取得して、コンソールに表示します。  
  
 [!code-csharp[Conceptual.Resources.Packaging#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.packaging/cs/example1.cs#1)] [!code-vb[Conceptual.Resources.Packaging#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.packaging/vb/example1.vb#1)]  
  
 その後、次のようにコマンド ラインから C# のソース コードをコンパイルできます。  
  
 **csc Example1.cs**  
  
 Visual Basic コンパイラのコマンドは次のとおりです。  
  
 **vbc Example1.vb**  
  
 メイン アセンブリにはリソースが埋め込まれていないため、`/resource` スイッチを使ってコンパイルする必要はありません。  
  
 言語がロシア語以外のシステムから例を実行すると、次の出力が表示されます。  
  
```  
Bon jour!  
```  
  
## <a name="suggested-packaging-alternative"></a>推奨されるパッケージ化の代替方法  
 時間や予算の制約により、アプリケーションがサポートするすべてのサブカルチャのリソース セットを作成できない場合があります。 そのような場合は、関連のあるすべてのサブカルチャで使うことができる親カルチャ用の単一のサテライト アセンブリを作成できます。 たとえば、地域固有の英語リソースを要求するユーザーによって取得される単一の英語サテライト アセンブリ (en) と、地域固有のドイツ語リソースを要求するユーザー用の単一のドイツ語サテライト アセンブリ (de) を提供することができます。 たとえば、ドイツ (de-DE)、オーストリア (de-AT)、スイス (de-CH) で話されるドイツ語の要求は、ドイツ語のサテライト アセンブリ (de) にフォールバックします。 既定のリソースは最終的なフォールバックであり、アプリケーションのほとんどのユーザーによって要求されるリソースであるため、これらのリソースは慎重に選択する必要があります。 この方法では、カルチャ固有性の低いリソースが配置されますが、アプリケーションのローカライズ費用を大幅に削減できます。  
  
## <a name="see-also"></a>関連項目  
 [デスクトップ アプリケーションのリソース](../../../docs/framework/resources/index.md)   
 [グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)   
 [リソース ファイルの作成](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md)   
 [サテライト アセンブリの作成](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md)

