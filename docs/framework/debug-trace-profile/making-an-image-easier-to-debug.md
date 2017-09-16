---
title: "イメージのデバッグの簡略化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- images [.NET Framework], debugging
- executable image for debugging
- debugging [.NET Framework], executable images for
ms.assetid: 7d90ea7a-150f-4f97-98a7-f9c26541b9a3
caps.latest.revision: 13
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e844cde5f33c1accb8addf953b5a72415f4dc301
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="making-an-image-easier-to-debug"></a>イメージのデバッグの簡略化
アンマネージ コードをコンパイルするときは、IDE スイッチまたはコマンド ライン オプションを使用して、デバッグ用の実行可能イメージを構成できます。 たとえば、Visual C++ で /**Zi** コマンド ライン オプションを使用すると、デバッグ シンボル ファイル (拡張子 .pdb) が生成されます。 同様に、/**Od** コマンド ライン オプションを使用すると、コンパイラは最適化処理を無効にします。 出力されるコードの処理速度は低下しますが、デバッグは簡単になるため、デバッグ時にはこれらのオプションを指定することをお勧めします。  
  
 .NET Framework マネージ コードをコンパイルするとき、Visual C++、Visual Basic、C# などのコンパイラは、そのソース プログラムをコンパイルして Microsoft Intermediate Language (MSIL) を生成します。 MSIL は、実行される直前にコンパイルされて、ネイティブなマシン語コードになります。 アンマネージ コードでは、IDE スイッチまたはコマンド ライン オプションを設定することにより、デバッグ用の実行可能イメージを構成できます。 さらに、ほとんど同じ方法で、デバッグ用の JIT コンパイルを構成することもできます。  
  
 このような目的で JIT を構成する場合、次の 2 つの要素が関係してきます。  
  
-   開発者は、JIT コンパイラに対し、追跡情報を生成するように要求できます。 追跡情報を生成すると、デバッガーは、MSIL のチェインをマシン語コードの対応部分に対応させたり、ローカル変数と関数の引数が格納される位置を追跡したりできるようになります。  .NET Framework Version 2.0 では、JIT コンパイラは常に追跡情報を生成します。そのため、要求する必要がありません。  
  
-   開発者は、JIT コンパイラに対し、出力するマシン語コードを最適化しないように要求できます。  
  
 通常、MSIL を生成するコンパイラは、指定された IDE スイッチまたはコマンド ライン オプション (/**Od** など) に基づいて、これらの JIT コンパイラ オプションを適切に設定します。  
  
 場合によっては、JIT コンパイラが生成するマシン語コードをデバッグしやすくするために、JIT コンパイラの動作の変更が必要となることがあります。 たとえば、製品版またはコントロールを最適化するために JIT 追跡情報の生成が必要となる場合などです。 このような場合は、初期化 (.ini) ファイルを使用します。  
  
 たとえば、MyApp.exe というアセンブリをデバッグする場合は、MyApp.exe と同じフォルダー内に MyApp.ini というテキスト ファイルを作成します。MyApp.ini ファイルには、次の 3 行を記述します。  
  
```  
[.NET Framework Debugging Control]  
GenerateTrackingInfo=1  
AllowOptimize=0  
```  
  
 各オプションの値として、0 または 1 を設定できます。記述しなかったオプションの値は、既定値の 0 に設定されます。 `GenerateTrackingInfo` を 1 に設定し、`AllowOptimize` を 0 に設定すると、デバッグが最も簡単になります。  
  
> [!NOTE]
>  .NET Framework Version 2.0 では、JIT コンパイラが `GenerateTrackingInfo` の値に関係なく常に追跡情報を生成しますが、`AllowOptimize` の値は引き続き効力を持ちます。 [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) を使用して最適化を行わずにネイティブ イメージをプリコンパイルする場合は、`AllowOptimize=0` が記述された .ini ファイルが、Ngen.exe 実行時にターゲット フォルダー内に存在している必要があります。 最適化を行わずにアセンブリをプリコンパイルした場合は、プリコンパイルされたコードを NGen.exe の **/uninstall** オプションを使用して削除したうえで、Ngen.exe を再度実行してコードを最適化してプリコンパイルする必要があります。 .ini ファイルがフォルダーにない場合は、Ngen.exe が既定でコードを最適化してプリコンパイルします。  
  
> [!NOTE]
>  アセンブリの設定は、<xref:System.Diagnostics.DebuggableAttribute?displayProperty=fullName> によって制御されます。 **DebuggableAttribute** には、2 つのフィールドがあり、それぞれは、JIT コンパイラが最適化処理を実行するかどうか、および追跡情報を生成するかどうかを設定します。 .NET Framework Version 2.0 では、JIT コンパイラは常に追跡情報を生成します。  
  
> [!NOTE]
>  製品版をビルドする場合、コンパイラは **DebuggableAttribute** のどちらのフィールドも設定しません。 JIT コンパイラの既定の動作では、最大のパフォーマンスを達成する、デバッグが最も困難なマシン語コードを生成します。 JIT 追跡を有効にすると、パフォーマンスが多少低下します。最適化処理を無効にすると、パフォーマンスは大幅に低下します。  
  
> [!NOTE]
>  **DebuggableAttribute** は、アセンブリに含まれる個々のモジュールではなく、アセンブリ全体に適用されます。 そのため開発ツールでは、アセンブリが既に作成されている場合は、カスタム属性をアセンブリのメタデータ トークン、または **System.Runtime.CompilerServices.AssemblyAttributesGoHere** というクラスに追加できる必要があります。 次に、ALink ツールによって、これらの **DebuggableAttribute** 属性は、各モジュールからこれらのモジュールが構成の一部となるアセンブリへと昇格されます。 競合が発生すると、ALink の操作は失敗します。  
  
> [!NOTE]
>  .NET Framework Version 1.0 では、**/clr** および **/Zi** コンパイラ オプションを指定すると、Microsoft Visual C++ コンパイラによって **DebuggableAttribute** が追加されます。 .NET Framework Version 1.1 では、**DebuggableAttribute** をコードに手動で追加するか、**/ASSEMBLYDEBUG** リンカー オプションを使用する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [デバッグ、トレース、およびプロファイリング](../../../docs/framework/debug-trace-profile/index.md)   
 [JIT アタッチ デバッグの有効化](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)   
 [プロファイルの有効化](http://msdn.microsoft.com/en-us/3b669676-f0e0-4ebf-8674-68986dd2020d)

