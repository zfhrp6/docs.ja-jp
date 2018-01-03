---
title: ".NET ネイティブの一般的なトラブルシューティング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee8c5e17-35ea-48a1-8767-83298caac1e8
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e92e99b978d12c32cc46b9133621875f35af634
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="net-native-general-troubleshooting"></a>.NET ネイティブの一般的なトラブルシューティング
このトピックでは、[!INCLUDE[net_native](../../../includes/net-native-md.md)]でアプリを開発するときに発生する可能性のある問題のトラブルシューティング方法を説明します。  
  
-   **問題:** ビルド出力ウィンドウが正しく更新されない。  
  
     **解決方法:** ビルド出力ウィンドウは、ビルドが完了するまで更新されません。 ビルドには数分かかる場合があるため、更新が表示されるまでに遅延が発生することがあります。  
  
-   **問題:** ARM 用のアプリの製品ビルド時間が長くなった。  
  
     **解決方法:** ARM デバイスにアプリを配置する場合、[!INCLUDE[net_native](../../../includes/net-native-md.md)] インフラストラクチャが呼び出されます。 このコンパイルは、リフレクションなどの非静的セマンティクスの実行が継続された状態で、多数の最適化を実行します。 さらに、パフォーマンスの最適化のために、.NET Framework でアプリが使用する部分は静的リンクされるため、コンパイルしてネイティブ コードにも含める必要があります。 このため、コンパイルの時間が長くなります。  
  
     ただし、標準的な開発用コンピューター上で、ほとんどのアプリの標準的なコンパイルにかかる時間は 1 分以内です。  通常、標準的な開発用コンピューターでは、.NET Framework のネイティブ イメージを生成するだけで数分かかります。  生成されるコードを改善するための最適化をすべて行い、.NET Framework を含めても、通常、アプリのビルド時間は 1 ～ 2 分です。  
  
     現在も、マルチスレッド コンパイルやその他の最適化を調査して、コンパイルのパフォーマンスを改善する取り組みが続いています。  
  
-   **問題:** アプリが [!INCLUDE[net_native](../../../includes/net-native-md.md)] を使用してコンパイルされたかどうかわからない。  
  
     **解決方法:** [!INCLUDE[net_native](../../../includes/net-native-md.md)] コンパイラが起動された場合、ビルド時間が長くなり、タスク マネージャーに ILC.exe や nutc_driver.exe などのさまざまな [!INCLUDE[net_native](../../../includes/net-native-md.md)] コンポーネント プロセスが表示されます。  
  
     [!INCLUDE[net_native](../../../includes/net-native-md.md)] でのプロジェクトのビルドが正常に完了すると、obj\\*config*\ *arch*\\*projectname*.ilc\out に出力が生成されます。最終的なネイティブ パッケージ コンテンツは、bin\\*arch*\\*config*\AppX にあります。 アプリを配置した場合、最終的なネイティブ パッケージ コンテンツは \bin\\*arch*\\*config*\AppX にあります。  
  
-   **問題:** .NET Native を使用してアプリをコンパイルすると、.NET Native を使用せずにコンパイルしたときにはスローされないランタイム例外 (通常は [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) または [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) 例外) がスローされる。  
  
     **解決方法:** これらの例外は、リフレクションを介して使用できるはずのメタデータまたは実装コードが .NET Native では提供されなかったためにスローされます  (詳細については、「[.NET ネイティブとコンパイル](../../../docs/framework/net-native/net-native-and-compilation.md)」を参照してください)。例外を取り除くには、[ランタイム ディレクティブ (rd.xml) ファイル](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)にエントリを追加して、.NET Native ツール チェーンがメタデータまたは実装コードを実行時に使用できるようにする必要があります。 次の 2 つのトラブルシューティング ツールを使用して、ランタイム ディレクティブ ファイルに追加する必要があるエントリを生成できます。  
  
    -   [MissingMetadataException トラブルシューティング ツール](http://dotnet.github.io/native/troubleshooter/type.html) (型の場合)。  
  
    -   [MissingMetadataException トラブルシューティング ツール](http://dotnet.github.io/native/troubleshooter/method.html) (メソッドの場合)。  
  
     詳細については、「[リフレクションおよび .NET ネイティブ](../../../docs/framework/net-native/reflection-and-net-native.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Windows ストア アプリの .NET ネイティブへの移行](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)
