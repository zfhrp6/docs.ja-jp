---
title: COM 相互運用機能によるデータのマーシャリング
ms.date: 09/07/2017
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0d94223223568efe921af3a340815a966cc6c6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388356"
---
# <a name="marshaling-data-with-com-interop"></a>COM 相互運用機能によるデータのマーシャリング
COM 相互運用は、マネージ コードから COM オブジェクトを使用すること、およびマネージ オブジェクトを COM に公開することの、両方の操作をサポートします。 COM との間でデータをマーシャリングする操作のサポートは広範で、ほとんどの場合、正しいマーシャリング動作が提供されます。  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] には、以下の COM 相互運用ツールが含まれています。  
  
-   [タイプ ライブラリ インポーター (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)、これは COM タイプ ライブラリを相互運用アセンブリに変換します。 このアセンブリから、相互運用マーシャリング サービスは、マネージ メモリとアンマネージ メモリ間のデータ マーシャリングを実行するラッパーを生成します。  
  
-   [タイプ ライブラリ エクスポーター (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)、これは COM タイプ ライブラリをアセンブリから生成して、メソッド呼び出しの際にマーシャリングを実行するラッパーを生成します。  
  
 以下のセクションは、マーシャラーに追加の型情報を提供できる (またはその必要がある) ときに、相互運用ラッパーをカスタマイズするためのプロセスについて説明するトピックにリンクしています。  
  
## <a name="in-this-section"></a>このセクションの内容  
[方法: ラッパを手動で作成する](how-to-create-wrappers-manually.md)   
マネージド ソース コードにおいて COM ラッパーを手動で作成する方法について説明します。 
 
 [方法: マネージ コード DCOM を WCF に移行する](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 最も安全なソリューションのために、マネージド DCOM コードを WCF に移行する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [COM のデータ型](https://msdn.microsoft.com/library/sak564ww(v=vs.100).aspx)  
 対応するマネージとアンマネージのデータ型を提供します。  
  
 [COM 呼び出し可能ラッパーのカスタマイズ](https://msdn.microsoft.com/library/3bwc828w(v=vs.100).aspx)  
 デザイン時に <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を使用して、データ型を明示的にマーシャリングする方法について説明します。  
  
 [ランタイム呼び出し可能ラッパーのカスタマイズ](https://msdn.microsoft.com/library/e753eftz(v=vs.100).aspx)  
 相互運用アセンブリで型のマーシャリング動作を調整する方法、および COM 型を手動で定義する方法について説明します。  
  
 [高度な COM 相互運用性](https://msdn.microsoft.com/library/bd9cdfyx(v=vs.100).aspx)  
 .NET Framework アプリケーションに COM コンポーネントを組み込む方法についての詳細情報へのリンクを示します。  
  
 [アセンブリからタイプ ライブラリへの変換の要約](https://msdn.microsoft.com/library/xk1120c3(v=vs.100).aspx)  
 アセンブリからタイプ ライブラリにエクスポート変換するプロセスについて説明します。  
  
 [タイプ ライブラリからアセンブリへの変換の要約](https://msdn.microsoft.com/library/k83zzh38(v=vs.100).aspx)  
 タイプ ライブラリからアセンブリにインポート変換するプロセスについて説明します。  
  
 [ジェネリック型を使用する相互運用](https://msdn.microsoft.com/library/ms229590(v=vs.100).aspx)  
 COM 相互運用性のジェネリック型を使用するとき、どのアクションがサポートされるかについて説明します。
