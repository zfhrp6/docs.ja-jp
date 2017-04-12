---
title: "COM 相互運用 (Visual Basic) の概要 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- interop assemblies
- COM interop, about COM interop
ms.assetid: 8bd62e68-383d-407f-998b-29aa0ce0fd67
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8866dbadca040c57ed2b59540dd2c341eb81758c
ms.lasthandoff: 03/13/2017

---
# <a name="introduction-to-com-interop-visual-basic"></a>COM 相互運用の概要 (Visual Basic)
コンポーネント オブジェクト モデル (COM) には、他のコンポーネントやアプリケーションをホストする機能を公開するオブジェクトことができます。 COM オブジェクトは、基本となる Windows 長年にわたってプログラミングされていますが、共通言語ランタイム (CLR) 用に設計されたアプリケーションでは、多くの利点が提供しています。  
  
 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アプリケーションが最終的に置き換わります com 開発 それまでは、使用またはを使用して COM オブジェクトを作成する必要があります[!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]します。 Com 相互運用性または*COM 相互運用機能*への移行中に既存の COM オブジェクトを使用することができます、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]独自のペースでします。  
  
 使用して、 [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] COM コンポーネントを作成するには、登録しない COM 相互運用機能を使用することができます。 これによって、どの DLL バージョンを有効にすると、1 つ以上のバージョンが、コンピューターにインストールされて、により、エンドユーザーは XCOPY または FTP を使用のコンピューターに適切なディレクトリにアプリケーションをコピーする実行できる場合を制御できます。 詳細については、次を参照してください。 [Registration-free COM 相互運用機能](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)です。  
  
## <a name="managed-code-and-data"></a>マネージ コードとデータ  
 用に開発されたコード、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]と呼ばれます*マネージ コード*、CLR によって使用されるメタデータが含まれています。 によって使用されるデータ[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アプリケーションと呼ばれる*管理データ*型の割り当て、メモリを再利用、および実行のチェックなど、ランタイムがデータに関連するタスクを管理するためです。 既定では、[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]マネージ コードとデータを使用して、アンマネージ コードと相互運用機能アセンブリを (このページの後半で説明します) を使用して COM オブジェクトのデータにアクセスすることができます。  
  
## <a name="assemblies"></a>アセンブリ  
 アセンブリの主な構成要素とは、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アプリケーションです。 これは、ビルド、バージョン管理、および&1; つまたは複数のファイルを含む単一の実装の単位として配置される機能のコレクションです。 各アセンブリには、アセンブリ マニフェストが含まれています。  
  
## <a name="type-libraries-and-assembly-manifests"></a>タイプ ライブラリとアセンブリのマニフェスト  
 タイプ ライブラリでは、メンバー名やデータ型など、COM オブジェクトの特性について説明します。 アセンブリのマニフェストの同じ機能を実行する[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アプリケーションです。 次の情報を示します。  
  
-   アセンブリの id、バージョン、カルチャ、およびデジタル署名します。  
  
-   アセンブリの実装を構成するファイルです。  
  
-   型と、アセンブリを構成するリソースです。 これには、アセンブリからエクスポートされるものが含まれています。  
  
-   他のアセンブリに依存関係をコンパイルします。  
  
-   アセンブリを正しく実行するために必要なアクセス許可です。  
  
 アセンブリおよびアセンブリのマニフェストの詳細については、次を参照してください。[アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)します。  
  
### <a name="importing-and-exporting-type-libraries"></a>インポートおよびタイプ ライブラリをエクスポートします。  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]タイプ ライブラリから情報をインポートできる Tlbimp ユーティリティが含まれています、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アプリケーションです。 Tlbexp ユーティリティを使用して、アセンブリからタイプ ライブラリを生成できます。  
  
 Tlbimp と Tlbexp については、次を参照してください。 [Tlbimp.exe (タイプ ライブラリ インポーター)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)と[Tlbexp.exe (タイプ ライブラリ エクスポーター)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)します。  
  
## <a name="interop-assemblies"></a>相互運用機能アセンブリ  
 相互運用機能アセンブリは[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]ブリッジ マネージ リソースとアンマネージ間するアセンブリ コードに、それと等価に COM オブジェクト メンバーのマッピング[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]メンバーを管理します。 によって作成された相互運用機能アセンブリ[!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)]の相互運用マーシャ リングなどの COM オブジェクトの使用の詳細を処理します。  
  
## <a name="interoperability-marshaling"></a>相互運用マーシャ リング  
 すべて[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]アプリケーションを使用するプログラミング言語に関係なく、オブジェクトの相互運用性を有効にする一般的な種類のセットを共有します。 パラメーターと COM オブジェクトの戻り値もマネージ コードで使用されるものとは異なるデータ型を使用します。 *相互運用マーシャ リング*パッケージ パラメーターと戻り値を等価のデータ型のプロセスは、COM オブジェクトとの間を移動します。 詳細については、次を参照してください。[相互運用マーシャ リング](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)します。  
  
## <a name="see-also"></a>関連項目  
 [COM 相互運用機能](../../../visual-basic/programming-guide/com-interop/index.md)   
 [チュートリアル: COM オブジェクトによる継承の実装](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)   
 [アンマネージ コードとの相互運用](https://msdn.microsoft.com/library/sd10k43k)   
 [相互運用性のトラブルシューティング](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)   
 [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Tlbimp.exe (タイプ ライブラリ インポーター)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)   
 [Tlbexp.exe (タイプ ライブラリ エクスポーター)](http://msdn.microsoft.com/library/a487d61b-d166-467b-a7ca-d8b52fbff42d)   
 [相互運用マーシャ リング](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [登録を必要としない COM 相互運用機能](http://msdn.microsoft.com/library/90f308b9-82dc-414a-bce1-77e0155e56bd)
