---
title: '方法: 発行者ポリシーを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 91971e4d41c3a54fa72ae73a3655dab650019676
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-create-a-publisher-policy"></a>方法: 発行者ポリシーを作成する
アプリケーションがアップグレード済みのアセンブリに発行者ポリシー ファイルを含めることによって、新しいバージョンのアセンブリを使用するアセンブリの販売元の状態のことができます。 発行者ポリシー ファイルは、アセンブリのリダイレクトやコード ベース設定を指定し、アプリケーション構成ファイルと同じフォーマットを使用します。 発行者ポリシー ファイルがアセンブリにコンパイルされ、グローバル アセンブリ キャッシュに配置します。  
  
 発行者ポリシーを作成するのには、3 つの手順があります。  
  
1.  発行者ポリシー ファイルを作成します。  
  
2.  発行者ポリシー アセンブリを作成します。  
  
3.  発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加します。  
  
 パブリッシャー ポリシー用のスキーマについては、「[アセンブリ バージョンのリダイレクト](../../../docs/framework/configure-apps/redirect-assembly-versions.md)です。 次の例は、発行者ポリシー ファイルの 1 つのバージョンをリダイレクトする`myAssembly`別にします。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
       <dependentAssembly>  
         <assemblyIdentity name="myAssembly"  
                           publicKeyToken="32ab4ba45e0a69a1"  
                           culture="en-us" />  
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->  
         <bindingRedirect oldVersion="1.0.0.0"  
                          newVersion="2.0.0.0"/>  
       </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
 コード ベースを指定する方法については、次を参照してください。[アセンブリの場所を指定する](../../../docs/framework/configure-apps/specify-assembly-location.md)です。  
  
## <a name="creating-the-publisher-policy-assembly"></a>発行者ポリシー アセンブリを作成します。  
 使用して、[アセンブリ リンカー (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md)発行者ポリシー アセンブリを作成します。  
  
#### <a name="to-create-a-publisher-policy-assembly"></a>発行者ポリシー アセンブリを作成するには  
  
1.  コマンド プロンプトで次のコマンドを入力します。  
  
     **al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*  
  
     このコマンドでは。  
  
    -   *PublisherPolicyFile*引数は、発行者ポリシー ファイルの名前。  
  
    -   *PublisherPolicyAssemblyFile*引数は、このコマンドを実行した結果、発行者ポリシー アセンブリの名前。 アセンブリ ファイル名は、形式に従う必要があります。  
  
         **policy.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    -   *KeyPairFile*引数は、キーのペアを含むファイルの名前。 アセンブリと同じキー ペアと発行者ポリシー アセンブリを署名する必要があります。  
  
    -   *ProcessorArchitecture*引数がプロセッサ固有のアセンブリの対象となるプラットフォームを識別します。  
  
        > [!NOTE]
        >  特定のプロセッサ アーキテクチャを対象とする機能は、.NET Framework version 2.0 の新機能です。  
  
     次のコマンドの作成と呼ばれる発行者ポリシー アセンブリ`policy.1.0.myAssembly`発行者ポリシー ファイルから呼び出す`pub.config`、内のキー ペアを使用してアセンブリに厳密な名前を割り当てます、`sgKey.snk`ファイル、および x86 の対象であるアセンブリを指定しますプロセッサ アーキテクチャです。  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     発行者ポリシー アセンブリは、それが適用されるアセンブリのプロセッサ アーキテクチャと一致する必要があります。 このため、アセンブリがある場合、<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A>の値<xref:System.Reflection.ProcessorArchitecture.MSIL>でそのアセンブリの発行者ポリシー アセンブリを作成する必要があります`/platform:anycpu`です。 個別に指定する必要があります各プロセッサ固有のアセンブリの発行者ポリシー アセンブリ。  
  
     このルールの結果が設定されて、アセンブリのプロセッサ アーキテクチャを変更するためにバージョン番号のメジャーまたはマイナー コンポーネントを変更する必要があります、正しいプロセッサ アーキテクチャと新しい発行者ポリシー アセンブリを指定することができます。 以前の発行者ポリシー アセンブリは、アセンブリが別のプロセッサ アーキテクチャを持つアセンブリを処理できません。  
  
     別の結果としては、プロセッサ アーキテクチャを常に指定されているので、.NET Framework の以前のバージョンを使用してコンパイルされたアセンブリの発行者ポリシー アセンブリを作成するバージョン 2.0 のリンカーを使用することはできません。  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加します。  
 使用して、[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加します。  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a>発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加するには  
  
1.  コマンド プロンプトで次のコマンドを入力します。  
  
     **gacutil/i***publisherPolicyAssemblyFile*   
  
     次のコマンドは、追加`policy.1.0.myAssembly.dll`グローバル アセンブリ キャッシュにします。  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  ない場合は、元の発行者ポリシー ファイル、アセンブリと同じディレクトリに、発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加できません。  
  
## <a name="see-also"></a>関連項目  
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [アプリの構成](../../../docs/framework/configure-apps/index.md)  
 [.NET Framework アプリの構成](http://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)  
 [ランタイム設定スキーマ](../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)  
 [アセンブリ バージョンのリダイレクト](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
