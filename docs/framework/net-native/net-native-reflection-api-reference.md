---
title: ".NET ネイティブ リフレクション API リファレンス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6c12c583d6c2040a093fb769803b79a6d88459ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="net-native-reflection-api-reference"></a>.NET ネイティブ リフレクション API リファレンス
[!INCLUDE[net_native](../../../includes/net-native-md.md)] には次の 3 つの新しい例外型が含まれています。 [System.Runtime.CompilerServices.MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)、 [System.Reflection.MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)、および [System.Reflection.MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)です。 3 つの例外型すべてについて、次の点に注意してください。  
  
 これらの型は、内部でのみ使用してください。  
 これら 3 つの例外型は、 [!INCLUDE[net_native](../../../includes/net-native-md.md)] ツール チェーンでのみ使用されます。 [!INCLUDE[net_native](../../../includes/net-native-md.md)] ツール チェーンがデータの欠落を検出し、プログラムの実行を続行できない場合に、これらの例外がスローされます。  
  
 これらの例外をコード内で処理しないでください。  
 これらの例外は、アプリケーションで必要なメタデータが存在しないこと ( [MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) 例外と [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外)、またはアプリケーションで必要な実装コードが欠落していること ( [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) 例外) のどちらかを示します。 これらの例外状態を修正するには、ランタイム ディレクティブ (.rd.xml) ファイルを変更して必要なメタデータまたは実装コードを実行時に使用できるようにします。 詳細については、「 [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)」を参照してください。 次の 2 つのトラブルシューティング ツールを使用して、 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) および [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) 例外を取り除くための適切なエントリをランタイム ディレクティブ ファイルに提供できます。  
  
-   [MissingMetadataException トラブルシューティング ツール](http://dotnet.github.io/native/troubleshooter/type.html) (型の場合)。  
  
-   [MissingMetadataException トラブルシューティング ツール](http://dotnet.github.io/native/troubleshooter/method.html) (メソッドの場合)。  
  
> [!NOTE]
>  このリファレンスでは、 [!INCLUDE[net_native](../../../includes/net-native-md.md)]に固有の 3 つの例外の型について説明しています。 .NET Framework の主要なリフレクション API に関するリファレンス ドキュメントについては、「 [System.Reflection 名前空間](http://msdn.microsoft.com/library/gg145033.aspx)」を参照してください。 .NET Framework の主要な相互運用 API に関するリファレンス ドキュメントについては、「 <xref:System.Runtime.InteropServices>」を参照してください。  
  
## <a name="systemreflection-namespace"></a>System.Reflection 名前空間  
 <xref:System.Reflection> 名前空間には、.NET Framework でリフレクションに使用される主要な型が含まれています。 [!INCLUDE[net_native](../../../includes/net-native-md.md)]の場合は、次の 2 つの新しい例外の種類も含まれています。  
  
|クラス|説明|  
|-----------|-----------------|  
|[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)|この例外は、存在しないメタデータを取得するためにリフレクションが使用された場合にスローされます。|  
|[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)|この例外は、型または型のメンバーのメタデータは使用可能だが、その実装が削除されている場合にスローされます。|  
  
 この名前空間の他の型に関するドキュメントについては、.NET Framework ドキュメント セットで <xref:System.Reflection> リファレンス ページを参照してください。  
  
## <a name="systemruntimecompilerservices-namespace"></a>System.Runtime.CompilerServices 名前空間  
 <xref:System.Runtime.CompilerServices> 名前空間には、言語コンパイラによって自動的にデザインされた型が含まれています。 [!INCLUDE[net_native](../../../includes/net-native-md.md)]の場合は、次の新しい例外の種類も含まれています。  
  
|クラス|説明|  
|-----------|-----------------|  
|[MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)|この例外は、手動マーシャリング メソッドが呼び出されたが、型のメタデータがスタティック分析でも、ランタイム ディレクティブ ファイルにも見つからない場合にスローされます。|  
  
 この名前空間の他の型に関するドキュメントについては、.NET Framework ドキュメント セットで <xref:System.Runtime.CompilerServices> リファレンス ページを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [MissingInteropDataException クラス](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)  
 [MissingMetadataException クラス](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)  
 [MissingRuntimeArtifactException クラス](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)  
 [はじめに](../../../docs/framework/net-native/getting-started-with-net-native.md)
