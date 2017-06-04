---
title: "アセンブリ名 | Microsoft Docs"
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
  - "アセンブリ [.NET Framework], 名前"
  - "名前 [.NET Framework], アセンブリ"
ms.assetid: 8f8c2c90-f15d-400e-87e7-a757e4f04d0e
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# アセンブリ名
アセンブリの名前は、メタデータに格納され、アセンブリのスコープおよびアプリケーションによる使用方法に大きく影響します。  厳密な名前を持つアセンブリは、アセンブリの名前、カルチャ、公開キー、およびバージョン番号を含む完全に限定された名前を持ちます。  この名前は通常、表示名と呼ばれ、ロード済みのアセンブリの場合には <xref:System.Reflection.Assembly.FullName%2A> プロパティを使用することによって取得できます。  
  
 ランタイムはこれらの情報を使用して、アセンブリを検索したり、同じ名前を持つ他のアセンブリと区別したりします。  たとえば、`myTypes` という厳密な名前を持つアセンブリが、次のような完全に限定された名前を持つ場合があります。  
  
```  
myTypes, Version=1.0.1234.0, Culture=en-US, PublicKeyToken=b77a5c561934e089c, ProcessorArchitecture=msil  
```  
  
> [!NOTE]
>  .NET Framework Version 2.0 では、プロセッサ アーキテクチャがアセンブリ ID に追加されて、アセンブリにプロセッサ固有のバージョンを作成できるようになっています。  たとえば、32 ビット プロセッサ固有のバージョン、64 ビット プロセッサ固有のバージョンのように、ID のプロセッサ アーキテクチャのみが異なっているアセンブリ バージョンを作成できます。  厳密な名前にはプロセッサ アーキテクチャは必要ありません。  詳細については、「<xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A?displayProperty=fullName>」を参照してください。  
  
 この例では、完全に限定された名前は `myTypes` アセンブリが公開キー トークンを含む厳密な名前を持ち、カルチャ値が US English であり、バージョン番号が 1.0.1234.0 であることを示します。  そのプロセッサ アーキテクチャは "msil" です。これは、オペレーティング システムとプロセッサに応じて 32 ビット コードまたは 64 ビット コードに Just\-In\-Time \(JIT\) コンパイルされることを意味します。  
  
 アセンブリ内で型を要求するコードは、完全に限定されたアセンブリ名を使用する必要があります。  これを完全限定バインディングと呼びます。  アセンブリ名だけを指定する部分バインディングは、.NET Framework でアセンブリを参照するときには使用できません。  
  
 .NET Framework を構成するアセンブリに対するすべてのアセンブリ参照には、アセンブリの完全限定名も含まれている必要があります。  たとえば、バージョン 1.0 の System.Data .NET Framework アセンブリを参照する場合は、次のようになります。  
  
```  
  
System.data, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
  
```  
  
 バージョンは、.NET Framework Version 1.0 に付属するすべての .NET Framework アセンブリのバージョン番号に相当します。  .NET Framework アセンブリでは、カルチャ値は常にニュートラルであり、公開キーは前の例の公開キーと同じです。  
  
 たとえば、構成ファイルにトレース リスナーを設定するアセンブリ参照を追加するには、システム .NET Framework アセンブリの完全限定名を含めます。  
  
```  
<add name="myListener" type="System.Diagnostics.TextWriterTraceListener, System, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
```  
  
> [!NOTE]
>  ランタイムは、アセンブリへのバインディング時にはアセンブリ名の大文字と小文字を区別しませんが、アセンブリ名で使用された大文字と小文字は保持されます。  [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] のいくつかのツールでは、アセンブリ名の大文字と小文字が区別されます。  大文字と小文字は区別されるものとしてアセンブリ名を管理するのが無難です。  
  
## アプリケーション コンポーネントの名前付け  
 ランタイムは、アセンブリを識別するときにファイル名を認識しません。  アセンブリの ID は、アセンブリ名、バージョン、カルチャおよび厳密な名前から構成され、ランタイムによって明確に認識される必要があります。  
  
 たとえば、myAssembly.dll という名前のアセンブリを参照する myAssembly.exe という名前のアセンブリがある場合は、myAssembly.exe を実行するとバインディングが正しく行われます。  しかし、別のアプリケーションが <xref:System.AppDomain.ExecuteAssembly%2A?displayProperty=fullName> メソッドを使用して myAssembly.exe を実行した場合は、myAssembly.exe が "myAssembly" に対するバインディングを要求しても、ランタイムは "myAssembly" が既に読み込まれているものと判断します。この場合、myAssembly.dll が読み込まれることはありません。  myAssembly.exe には要求された型が含まれていないため、<xref:System.TypeLoadException> が発生します。  
  
 この問題を回避するには、アプリケーション内で複数のアセンブリが同じアセンブリ名を持たないようにするか、または同じ名前を持つアセンブリをそれぞれ異なるディレクトリに配置します。  
  
> [!NOTE]
>  厳密な名前付きアセンブリをグローバル アセンブリ キャッシュに配置する場合、.exe や .dll などのファイル名の拡張子を除いたアセンブリのファイル名とアセンブリ名とが一致している必要があります。  たとえば、アセンブリのファイル名が myAssembly.dll である場合、アセンブリ名は myAssembly である必要があります。  ルート アプリケーション ディレクトリ内にだけ配置されるプライベート アセンブリは、ファイル名と異なるアセンブリ名を持つことができます。  
  
## 参照  
 [方法 : アセンブリの完全修飾名を特定する](../../../docs/framework/app-domains/how-to-determine-assembly-fully-qualified-name.md)   
 [アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md)   
 [厳密な名前付きアセンブリ](../../../docs/framework/app-domains/strong-named-assemblies.md)   
 [グローバル アセンブリ キャッシュ](../../../docs/framework/app-domains/gac.md)   
 [ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)   
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)