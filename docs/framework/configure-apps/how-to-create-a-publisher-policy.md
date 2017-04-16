---
title: "方法 : 発行者ポリシーを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GAC (グローバル アセンブリ キャッシュ), 発行者ポリシー アセンブリ"
  - "グローバル アセンブリ キャッシュ, 発行者ポリシー アセンブリ"
  - "発行者ポリシー アセンブリ"
  - "発行者ポリシー ファイル"
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
caps.latest.revision: 15
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 15
---
# 方法 : 発行者ポリシーを作成する
アセンブリの販売元は、アップグレードしたアセンブリに発行者ポリシー ファイルを含めることにより、より新しいバージョンのアセンブリを使用してアプリケーションを実行するように指示できます。  発行者ポリシー ファイルには、アセンブリのリダイレクトやコード ベース設定を指定し、その書式にはアプリケーション構成ファイルと同じ書式を使用します。  発行者ポリシーファイルをコンパイルしてアセンブリを生成し、グローバル アセンブリ キャッシュに配置します。  
  
 発行者ポリシーは、次の手順で作成します。  
  
1.  発行者ポリシー ファイルを作成します。  
  
2.  発行者ポリシー アセンブリを作成します。  
  
3.  その発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加します。  
  
 発行者ポリシーのスキーマについては、「[アセンブリ バージョンのリダイレクト](../../../docs/framework/configure-apps/redirect-assembly-versions.md)」を参照してください。  `myAssembly` のあるバージョンを別のバージョンにリダイレクトする発行者ポリシー ファイルを次の例に示します。  
  
```  
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
  
 コード ベースの指定方法については、「[アセンブリの場所の指定](../../../docs/framework/configure-apps/specify-assembly-location.md)」を参照してください。  
  
## 発行者ポリシー アセンブリの作成  
 発行者ポリシー アセンブリを作成するには、[アセンブリ リンカー \(Al.exe\)](../../../docs/framework/tools/al-exe-assembly-linker.md) を使用します。  
  
#### ライブラリ アセンブリを作成するには  
  
1.  コマンド プロンプトに次のコマンドを入力します。  
  
     **al \/link:** *publisherPolicyFile* **\/out:** *publisherPolicyAssemblyFile* **\/keyfile:** *keyPairFile* **\/platform:** *processorArchitecture*  
  
     上記のコマンドには、次の引数を指定します。  
  
    -   *publisherPolicyFile* 引数には、発行者ポリシー ファイルの名前を指定します。  
  
    -   *publisherPolicyAssemblyFile* 引数には、このコマンドを実行した結果作成される発行者ポリシー アセンブリの名前を指定します。  アセンブリ ファイルの名前は、次の書式にする必要があります。  
  
         **policy.** *majorNumber* **.** *minorNumber* **.** *mainAssemblyName* **.dll**  
  
    -   *keyPairFile* 引数には、キー ペアを含むファイルの名前を指定します。  アセンブリと発行者ポリシー アセンブリには、同じキー ペアで署名する必要があります。  
  
    -   *processorArchitecture* 引数には、プロセッサ固有のアセンブリが対象とするプラットフォームを指定します。  
  
        > [!NOTE]
        >  .NET Framework Version 2.0 では、特定のプロセッサ アーキテクチャを対象にできるようになりました。  
  
     `policy.1.0.myAssembly` という発行者ポリシー アセンブリを発行者ポリシー ファイル `pub.config` から作成し、そのアセンブリに `sgKey.snk` ファイル内のキー ペアを使用して厳密な名前を割り当て、x86 プロセッサ アーキテクチャを対象とするアセンブリを指定するコマンドを次に示します。  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     発行者ポリシー アセンブリは、適用先アセンブリのプロセッサ アーキテクチャと一致している必要があります。  したがって、アセンブリの <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> 値が <xref:System.Reflection.ProcessorArchitecture> である場合、そのアセンブリの発行者ポリシー アセンブリは `/platform:anycpu` を使用して作成されている必要があります。  ポリシー固有のアセンブリごとに個別の発行者ポリシー アセンブリを指定する必要があります。  
  
     この規則により、アセンブリのプロセッサ アーキテクチャを変更する場合、バージョン番号のメジャー部分またはマイナー部分を変更して、正しいプロセッサ アーキテクチャで新しい発行者ポリシー アセンブリを指定する必要があります。  アセンブリに異なるプロセッサ アーキテクチャが指定されていると、古い発行者ポリシー アセンブリがアセンブリにサービスを提供できません。  
  
     また、この規則により、常にプロセッサ アーキテクチャが指定されるため、以前のバージョンの .NET Framework を使用してコンパイルしたアセンブリに対しては、バージョン 2.0 のリンカーを使用して発行者ポリシー アセンブリを作成できません。  
  
## 発行者ポリシー アセンブリのグローバル アセンブリ キャッシュへの追加  
 発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加するには、[グローバル アセンブリ キャッシュ ツール \(Gacutil.exe\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用します。  
  
#### 発行者ポリシー アセンブリをグローバル アセンブリ キャッシュに追加するには  
  
1.  コマンド プロンプトに次のコマンドを入力します。  
  
     **gacutil \/i**  *publisherPolicyAssemblyFile*  
  
     `policy.1.0.myAssembly.dll` をグローバル アセンブリ キャッシュに追加するコマンドを次に示します。  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  発行者ポリシー アセンブリは、元の発行者ポリシー ファイルがアセンブリと同じディレクトリにある場合を除き、グローバル アセンブリ キャッシュに追加できません。  
  
## 参照  
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)   
 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [アプリの構成](../../../docs/framework/configure-apps/index.md)   
 [Configuring .NET Framework Apps](http://msdn.microsoft.com/ja-jp/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)   
 [ランタイム設定スキーマ](../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)   
 [アセンブリ バージョンのリダイレクト](../../../docs/framework/configure-apps/redirect-assembly-versions.md)