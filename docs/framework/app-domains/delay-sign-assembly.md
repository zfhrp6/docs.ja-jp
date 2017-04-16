---
title: "アセンブリへの遅延署名 | Microsoft Docs"
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
  - "延期 (アセンブリ署名の)"
  - "署名 (アセンブリに)"
  - "アセンブリ [.NET Framework]、署名"
  - "厳密な名前を付けたアセンブリ、遅延 (アセンブリ署名の)"
  - "部分アセンブリ署名"
ms.assetid: 9d300e17-5bf1-4360-97da-2aa55efd9070
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# アセンブリへの遅延署名
開発者側が日常的にアクセスしないキー ペアを、組織で厳重に保護できます。  公開キーは多くのユーザーが使用できることもありますが、秘密キーにアクセスできるユーザーはごくわずかです。  厳密な名前付きのアセンブリを開発する場合、厳密な名前付きの対象アセンブリを参照する各アセンブリには、対象アセンブリに厳密な名前を付けるために使用された公開キーのトークンを格納します。  そのためには、開発プロセス中に公開キーを使用できる必要があります。  
  
 ビルド時に遅延署名または部分署名を使用すると、ポータブル実行可能 \(PE\) ファイルの領域を厳密な名前の署名のために予約できます。しかし、実際の署名は後の段階 \(通常はアセンブリの出荷直前\) まで遅れます。  
  
 アセンブリに遅延署名する手順の概要を次に示します。  
  
1.  最終的な署名を行う組織からキー ペアの公開キー部分を取得します。  通常、このキーは .snk ファイル形式です。このファイルは、[!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] に用意されている[厳密名ツール \(Sn.exe\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) を使用して作成できます。  
  
2.  <xref:System.Reflection> の 2 つのカスタム属性を使用して、アセンブリのソース コードに注釈を付けます。  
  
    -   <xref:System.Reflection.AssemblyKeyFileAttribute> は、公開キーを格納するファイルの名前をパラメーターとしてコンストラクターに渡します。  
  
    -   <xref:System.Reflection.AssemblyDelaySignAttribute> は、遅延署名を使用していることを示すために、**true** をパラメーターとしてコンストラクターに渡します。  たとえば、次のようになります。  
  
         [!code-cpp[AssemblyDelaySignAttribute#4](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cpp/source2.cpp#4)]
         [!code-csharp[AssemblyDelaySignAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyDelaySignAttribute/cs/source2.cs#4)]
         [!code-vb[AssemblyDelaySignAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyDelaySignAttribute/vb/source2.vb#4)]  
  
3.  コンパイラは、公開キーをアセンブリ マニフェストに挿入し、PE ファイル内の領域を完全な厳密な名前の署名のために予約します。  実際の公開キーはアセンブリのビルド中に格納してください。これにより、このアセンブリを参照するほかのアセンブリが、それぞれのアセンブリ参照に格納するキーを取得できるようになります。  
  
4.  アセンブリには有効な厳密な名前の署名がないため、厳密な名前の署名の検証をオフにする必要があります。  検証をオフにするには、厳密名ツールで **–Vr** オプションを使用します。  
  
     アセンブリ `myAssembly.dll` の検証をオフにする例を次に示します。  
  
    ```  
    sn –Vr myAssembly.dll  
    ```  
  
     レジストリ ファイルを作成するために使用 **–Vk** オプション厳密名ツール、RISC コンピューター \(ARM\) の詳細マイクロプロセッサなどの実行できないプラットフォームの検証を無効にする。  検証をオフにするコンピューターのレジストリにレジストリ ファイルをインポートします。  次の例では `myAssembly.dll`のレジストリ ファイルを作成します。  
  
    ```  
    sn –Vk myRegFile.reg myAssembly.dll  
    ```  
  
     **–Vr** または **–Vk** オプションを使用すると、必要に応じてテスト キーの署名の .snk ファイルを含めることができます。  
  
    > [!CAUTION]
    >  開発時にだけ **\-Vr** または **–Vk** オプションを使用します。  検証省略リストにアセンブリを追加すると、セキュリティ上の脆弱性が生じます。  悪意のあるアセンブリは、検証省略リストに追加されたアセンブリの完全限定アセンブリ名 \(アセンブリ名、バージョン、カルチャ、および公開キー トークン\) を使用することによって、その ID を偽装できます。  これによって、悪意のあるアセンブリの検証も省略できます。  
  
    > [!NOTE]
    >  64 ビット コンピューターで Visual Studio を使用して開発しているときに遅延署名を使用し、**\[Any CPU\]** のアセンブリをコンパイルする場合は、**\-Vr** オプションを 2 回適用することが必要な場合があります \(Visual Studio では、**\[Any CPU\]** は **\[プラットフォーム ターゲット\]** ビルド プロパティの値です。コマンド ラインからコンパイルする場合は、これが既定です\)。コマンド ラインまたはファイル エクスプローラーからアプリケーションを実行するには、アセンブリに **\-Vr** オプションを適用するために [Sn.exe \(厳密名ツール\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) の 64 ビット バージョンを使用します。  デザイン時にアセンブリを Visual Studio に読み込むには \(たとえば、アセンブリに、アプリケーションの他のアセンブリで使用されているコンポーネントが含まれている場合\)、32 ビット バージョンの厳密名ツールを使用します。  これは、Just\-In\-Time \(JIT\) コンパイラが、アセンブリがコマンド ラインから実行される場合にはアセンブリを 64 ビット ネイティブ コードにコンパイルし、アセンブリがデザイン時環境に読み込まれる場合には 32 ビット ネイティブ コードにコンパイルするためです。  
  
5.  その後、通常は出荷の直前に、アセンブリを組織の署名機関に送信し、**–R** オプション付きで厳密名ツールを使用して、実際の厳密な名前の署名を取得します。  
  
     `sgKey.snk` キー ペアを使用して厳密な名前でアセンブリ `myAssembly.dll` に署名する例を次に示します。  
  
    ```  
    sn -R myAssembly.dll sgKey.snk  
    ```  
  
## 参照  
 [アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md)   
 [方法 : 公開キーと秘密キーのキー ペアを作成する](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)   
 [Sn.exe \(厳密名ツール\)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)   
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)