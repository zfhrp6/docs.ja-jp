---
title: "タイプ ライブラリのアセンブリとしてのインポート | Microsoft Docs"
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
  - "COM 相互運用機能, 公開 (COM コンポーネントを)"
  - "COM 相互運用機能, インポート (タイプ ライブラリの)"
  - "カスタム ラッパー"
  - "公開 (.NET Framework に COM コンポーネントを)"
  - "インポート (タイプ ライブラリの)"
  - "相互運用 (アンマネージ コードとの), 公開 (COM コンポーネントを)"
  - "相互運用 (アンマネージ コードとの), インポート (タイプ ライブラリの)"
  - "メタデータ"
  - "タイプ ライブラリ"
  - "タイプ ライブラリ インポーター"
  - "型のメタデータ"
  - "TypeLibConverter クラス, インポート (タイプ ライブラリをアセンブリとして)"
ms.assetid: d1898229-cd40-426e-a275-f3eb65fbc79f
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# タイプ ライブラリのアセンブリとしてのインポート
COM 型の定義は、通常はタイプ ライブラリに存在します。  これに対し、CLS 準拠のコンパイラは、型メタデータをアセンブリ内に生成します。  型情報に関するこれら 2 つのソースは、まったく異なっています。  このトピックでは、タイプ ライブラリからメタデータを生成する方法を説明します。  結果として生成されるアセンブリは相互運用機能アセンブリと呼ばれ、それに含まれる型情報によって .NET Framework アプリケーションは COM 型を使用できます。  
  
 この型情報をアプリケーションで使用する方法には、次の 2 つがあります。  
  
-   デザイン時のみの相互運用機能アセンブリを使用する: [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、相互運用機能アセンブリから実行可能ファイルに型情報を埋め込むようにコンパイラに指示できます。  コンパイラは、アプリケーションが使用する型情報のみを埋め込みます。  アプリケーションで相互運用機能アセンブリを配置する必要はありません。  この手法を使用することをお勧めします。  
  
-   相互運用機能アセンブリを配置する: 相互運用機能アセンブリへの標準の参照を作成できます。  この場合、アプリケーションで相互運用機能アセンブリを配置する必要があります。  この手法を採用する場合に、プライベートの COM コンポーネントを使用しないときは、必ず、マネージ コードに組み込む COM コンポーネントの作成者が発行したプライマリ相互運用機能アセンブリ \(PIA\) を参照してください。  プライマリ相互運用機能アセンブリの作成と使用の詳細については、「[プライマリ相互運用機能アセンブリ](http://msdn.microsoft.com/ja-jp/b977a8be-59a0-40a0-a806-b11ffba5c080)」を参照してください。  
  
 デザイン時のみの相互運用機能アセンブリを使用するとき、COM コンポーネントの作成者が発行したプライマリ相互運用機能アセンブリから型情報を埋め込むことができます。  ただし、アプリケーションで相互運用機能アセンブリを配置する必要はありません。  
  
 COM コンポーネントのすべての機能を使用するアプリケーションはほとんどないため、デザイン時のみの相互運用機能アセンブリを使用するとアプリケーションのサイズが小さくなります。  コンパイラは、型情報を埋め込むとき、非常に効率的に処理を実行します。アプリケーションが COM インターフェイスの一部のメソッドしか使用しない場合、コンパイラは使用されないメソッドの埋め込みは行いません。  埋め込み型情報を持つアプリケーションが他の同様のアプリケーションと対話したり、プライマリ相互運用機能アセンブリを使用するアプリケーションと対話したりするとき、共通言語ランタイムは型等価性の規則を使用して、同じ名前を持つ 2 つの型が同じ COM 型を表しているかどうかを確認します。  COM オブジェクトを使用するために、これらの規則について理解しておく必要はありません。  この規則に関心がある場合は、「[型の等価性と埋め込まれた相互運用機能型](../../../docs/framework/interop/type-equivalence-and-embedded-interop-types.md)」を参照してください。  
  
## メタデータの生成  
 COM タイプ ライブラリは、Loanlib.tlb などの .tlb 拡張子を持つスタンドアロンのファイルである場合があります。  .dll ファイルまたは .exe ファイルのリソース セクションに埋め込まれるタイプ ライブラリもあります。  タイプ ライブラリ情報のその他のソースとして、.olb ファイルと .ocx ファイルがあります。  
  
 対象の COM 型の実装を含むタイプ ライブラリの場所を特定したら、次のいずれかの方法で型メタデータを格納する相互運用機能アセンブリを生成できます。  
  
-   Visual Studio  
  
     Visual Studio を使用して、タイプ ライブラリの COM 型をアセンブリのメタデータに自動的に変換します。  手順については、「[方法: タイプ ライブラリへの参照を追加する](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md)」および「[チュートリアル: Microsoft Office アセンブリからの型情報の埋め込み](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)」を参照してください。  
  
-   [タイプ ライブラリ インポーター \(Tlbimp.exe\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)  
  
     タイプ ライブラリ インポーターには、生成される相互運用ファイル内のメタデータを調整するコマンド ライン オプションが用意されていて、既存のタイプ ライブラリから型をインポートし、相互運用機能アセンブリおよび名前空間を生成します。  手順については、「[方法 : 相互運用アセンブリをタイプ ライブラリから生成する](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)」を参照してください。  
  
-   <xref:System.Runtime.InteropServices.TypeLibConverter?displayProperty=fullName> クラス  
  
     このクラスは、タイプ ライブラリ内のコクラスとインターフェイスをアセンブリ内のメタデータに変換するメソッドを提供します。  これは、Tlbimp.exe と同じメタデータ出力を生成します。  ただし、<xref:System.Runtime.InteropServices.TypeLibConverter> クラスは、Tlbimp.exe とは異なり、インメモリ タイプ ライブラリをメタデータに変換できます。  
  
-   カスタム ラッパー  
  
     タイプ ライブラリが利用できないか、または無効である場合には、1 つの選択肢として、マネージ ソース コードでクラスまたはインターフェイスの複製定義を作成する方法があります。  その後で、ランタイムを対象とするコンパイラでソース コードをコンパイルし、アセンブリ内にメタデータを生成します。  
  
     COM 型を手動で定義するには、次の項目にアクセスできる必要があります。  
  
    -   定義するコクラスおよびインターフェイスの詳細な説明。  
  
    -   適切な .NET Framework クラス定義を生成できる、C\# コンパイラなどのコンパイラ。  
  
    -   タイプ ライブラリからアセンブリへの変換規則に関する知識。  
  
     カスタム ラッパーを作成することは、高度な手法です。  カスタム ラッパーを生成する方法の詳細については、「[標準ラッパーのカスタマイズ](http://msdn.microsoft.com/ja-jp/c40d089b-6a3c-41b5-a20d-d760c215e49d)」を参照してください。  
  
 COM 相互運用機能のインポート プロセスの詳細については、「[タイプ ライブラリからアセンブリへの変換の要約](http://msdn.microsoft.com/ja-jp/bf3f90c5-4770-4ab8-895c-3ba1055cc958)」を参照してください。  
  
## 参照  
 <xref:System.Runtime.InteropServices.TypeLibConverter>   
 [.NET Framework への COM コンポーネントの公開](../../../docs/framework/interop/exposing-com-components.md)   
 [Type Library to Assembly Conversion Summary](http://msdn.microsoft.com/ja-jp/bf3f90c5-4770-4ab8-895c-3ba1055cc958)   
 [Tlbimp.exe \(タイプ ライブラリ インポーター\)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)   
 [Customizing Standard Wrappers](http://msdn.microsoft.com/ja-jp/c40d089b-6a3c-41b5-a20d-d760c215e49d)   
 [Using COM Types in Managed Code](http://msdn.microsoft.com/ja-jp/1a95a8ca-c8b8-4464-90b0-5ee1a1135b66)   
 [相互運用プロジェクトのコンパイル](../../../docs/framework/interop/compiling-an-interop-project.md)   
 [相互運用アプリケーションの配置](../../../docs/framework/interop/deploying-an-interop-application.md)   
 [方法: タイプ ライブラリへの参照を追加する](../../../docs/framework/interop/how-to-add-references-to-type-libraries.md)   
 [方法: 相互運用機能アセンブリをタイプ ライブラリから生成する](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)   
 [チュートリアル: Microsoft Office アセンブリからの型情報の埋め込み](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)