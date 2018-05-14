---
title: '方法 : 厳密な名前のアセンブリを参照する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7f78fff50d1a227061076790ad77f17debe3f690
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-reference-a-strong-named-assembly"></a>方法 : 厳密な名前のアセンブリを参照する
通常、厳密な名前付きアセンブリ内にある型またはリソースを参照するプロセスは透過的です。 コンパイル時 (事前バインディング) または実行時に参照を作成できます。  
  
 コンパイル時参照は、あるアセンブリが別のアセンブリを明示的に参照することをコンパイラに対して指定するときに発生します。 コンパイル時参照を使用する場合、コンパイラは対象の厳密な名前付きアセンブリの公開キーを自動的に取得し、その公開キーをコンパイルされるアセンブリのアセンブリ参照内に自動的に配置します。  
  
> [!NOTE]
>  厳密な名前のアセンブリは、他の厳密な名前のアセンブリでのタイプだけを使用できます。 それ以外の場合は、厳密な名前のアセンブリのセキュリティが損なわれます。  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a>厳密な名前付きアセンブリへのコンパイル時参照を作成するには  
  
1.  コマンド プロンプトに次のコマンドを入力します。  
  
     \<*compiler command*> **/reference:**\<*assembly name*>  
  
     このコマンドで、*compiler command* は、使用している言語のコンパイラ コマンドです。*assembly name* は、参照される厳密な名前付きアセンブリの名前です。 ライブラリ アセンブリを作成するための **/t:library** オプションなどの他のコンパイラ オプションも使用できます。  
  
 `myAssembly.cs` というコード モジュールから厳密な名前付きアセンブリ `myLibAssembly.dll` を参照するアセンブリ `myAssembly.dll` を作成する例を次に示します。  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a>厳密な名前付きアセンブリへの実行時参照を作成するには  
  
1.  <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> メソッドまたは <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> メソッドを使用するなどの方法で、実行時に厳密な名前付きアセンブリ参照を作成する場合は、参照される厳密な名前付きアセンブリの表示名を使用する必要があります。 表示名の構文は次のとおりです。  
  
     \<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*>  
  
     例:  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     この例では、`PublicKeyToken` は 16 進形式の公開キートークンです。 カルチャの値がない場合は、`Culture=neutral` を使用します。  
  
 この情報を <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> メソッドで使用する方法を次の例に示します。  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 特定のアセンブリの 16 進形式の公開キーと公開キー トークンは、次の[厳密名 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) コマンドを使用して出力できます。  
  
 **sn -Tp \<** *assembly* **>**  
  
 公開キーファイルがある場合は、代わりに次のコマンドを使用できます (コマンド ライン オプションの大文字と小文字の違いに注意してください)。  
  
 **sn -tp \<** *assembly* **>**  
  
## <a name="see-also"></a>参照  
 [厳密な名前付きアセンブリの作成と使用](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
