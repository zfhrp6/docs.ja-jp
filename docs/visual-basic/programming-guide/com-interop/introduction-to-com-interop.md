---
title: COM 相互運用の概要 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interop assemblies
- COM interop [Visual Basic], about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
ms.openlocfilehash: 639b621215f25bc1042274a92a21fca2985e5918
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644397"
---
# <a name="introduction-to-com-interop-visual-basic"></a>COM 相互運用の概要 (Visual Basic)
コンポーネント オブジェクト モデル (COM) は、他のコンポーネントおよびホスト アプリケーションには、その機能を公開するオブジェクトを付与します。 COM オブジェクトは、Windows 長年にわたってプログラミングの基本されていますが、共通言語ランタイム (CLR) 用に設計されたアプリケーションでは、多くの利点が提供しています。  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] アプリケーションが最終的に置き換わります com 開発 それまでは、使用または Visual Studio を使用して COM オブジェクトを作成する必要があります。 Com 相互運用性または*COM 相互運用*への移行中に既存の COM オブジェクトを使用することができます、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]独自のペースでします。  
  
 使用して、 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] COM コンポーネントを作成するには、登録しない COM 相互運用を使用することができます。 場合に複数のバージョンがコンピューターでは、インストールされている、エンドユーザーは XCOPY または FTP を使用のコンピューターに適切なディレクトリにアプリケーションをコピーする実行できる DLL バージョンが有効になっているかを制御できます。 詳細については、次を参照してください。[登録しない COM 相互運用](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)です。  
  
## <a name="managed-code-and-data"></a>マネージ コードとデータ  
 用に開発されたコード、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]呼びます*マネージ コード*、CLR によって使用されるメタデータが含まれています。 によって使用されるデータ[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アプリケーションと呼びます*管理データ*の割り当てとメモリを再利用を実行する型のチェックなど、ランタイムがデータに関連するタスクを管理するためです。 既定では、Visual Basic .NET を使用してマネージ コードと、データが、アンマネージ コードと相互運用機能アセンブリを (このページの後半で説明します) を使用して COM オブジェクトのデータにアクセスすることができます。  
  
## <a name="assemblies"></a>アセンブリ  
 アセンブリは、の主なビルド ブロック、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アプリケーションです。 これは、ビルド、バージョン管理、および 1 つまたは複数のファイルを含む単一の実装の単位として配置される機能のコレクション。 各アセンブリには、アセンブリ マニフェストが含まれています。  
  
## <a name="type-libraries-and-assembly-manifests"></a>タイプ ライブラリとアセンブリのマニフェスト  
 タイプ ライブラリでは、メンバー名とデータ型など、COM オブジェクトの特性について説明します。 アセンブリ マニフェストの同じ機能を実行する[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アプリケーションです。 次の項目について例を示します。  
  
-   アセンブリの id、バージョン、カルチャ、およびデジタル署名します。  
  
-   アセンブリの実装を構成するファイル。  
  
-   型およびアセンブリを構成するリソース。 これには、アセンブリからエクスポートされるものが含まれています。  
  
-   他のアセンブリに対する依存関係をコンパイルします。  
  
-   アセンブリを正しく実行するために必要なアクセス許可です。  
  
 アセンブリおよびアセンブリ マニフェストの詳細については、次を参照してください。[アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)です。  
  
### <a name="importing-and-exporting-type-libraries"></a>インポートおよびタイプ ライブラリをエクスポートします。  
 Visual Studio にタイプ ライブラリから情報をインポートできる Tlbimp ユーティリティが含まれています、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アプリケーションです。 Tlbexp ユーティリティを使用して、アセンブリからタイプ ライブラリを生成できます。  
  
 Tlbimp と Tlbexp については、次を参照してください。 [Tlbimp.exe (タイプ ライブラリ インポーター)](../../../framework/tools/tlbimp-exe-type-library-importer.md)と[Tlbexp.exe (タイプ ライブラリ エクスポーター)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)です。  
  
## <a name="interop-assemblies"></a>相互運用機能アセンブリ  
 相互運用機能アセンブリは[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]ブリッジ マネージ リソースとアンマネージ間をアセンブリ コードに、マッピングの COM オブジェクトのメンバーに相当する[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]メンバーを管理します。 Visual Basic .NET で作成された相互運用機能アセンブリは、多くの相互運用マーシャ リングなどの COM オブジェクトの操作の詳細を処理します。  
  
## <a name="interoperability-marshaling"></a>相互運用マーシャ リング  
 すべて[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アプリケーションを使用するプログラミング言語に関係なく、オブジェクトの相互運用性を有効にする一般的な種類のセットを共有します。 パラメーターおよび COM オブジェクトの戻り値は、マネージ コードで使用されるものとは異なるデータ型を使用して場合があります。 *相互運用マーシャ リング*はパッケージ パラメーターと同等のデータ型に戻り値の処理、COM オブジェクトとの間を移動します。 詳細については、次を参照してください。[相互運用マーシャ リング](../../../framework/interop/interop-marshaling.md)です。  
  
## <a name="see-also"></a>関連項目  
 [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md)  
 [チュートリアル : COM オブジェクトによる継承の実装](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)  
 [アンマネージ コードとの相互運用](../../../framework/interop/index.md)  
 [相互運用性のトラブルシューティング](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)  
 [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Tlbimp.exe (タイプ ライブラリ インポーター)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 [Tlbexp.exe (タイプ ライブラリ エクスポーター)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)  
 [相互運用マーシャリング](../../../framework/interop/interop-marshaling.md)  
 [登録を必要としない COM 相互運用機能](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)
