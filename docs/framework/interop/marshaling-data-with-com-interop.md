---
title: "COM 相互運用機能によるデータのマーシャリング"
ms.custom: 
ms.date: 09/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, data marshaling
- marshaling data, COM interop
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2def27790a1727bda524b8c14a93f7b78127a569
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="marshaling-data-with-com-interop"></a>COM 相互運用機能によるデータのマーシャリング
COM 相互運用は、マネージ コードから COM オブジェクトを使用すること、およびマネージ オブジェクトを COM に公開することの、両方の操作をサポートします。 COM との間でデータをマーシャリングする操作のサポートは広範で、ほとんどの場合、正しいマーシャリング動作が提供されます。  
  
 [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] には、以下の COM 相互運用ツールが含まれています。  
  
-   [タイプ ライブラリ インポーター (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md)、これは COM タイプ ライブラリを相互運用アセンブリに変換します。 このアセンブリから、相互運用マーシャリング サービスは、マネージ メモリとアンマネージ メモリ間のデータ マーシャリングを実行するラッパーを生成します。  
  
-   [タイプ ライブラリ エクスポーター (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)、これは COM タイプ ライブラリをアセンブリから生成して、メソッド呼び出しの際にマーシャリングを実行するラッパーを生成します。  
  
 次のセクションでは、ことができます (または必要があります) を指定すると追加の型情報では、マーシャラーは、相互運用ラッパーをカスタマイズするためのプロセスを説明するトピックへリンクします。  
  
## <a name="in-this-section"></a>このセクションの内容  
[方法: 手動でラッパーを作成します。](how-to-create-wrappers-manually.md)   
マネージ ソース コードで COM ラッパーを手動で作成する方法について説明します。 
 
 [方法: マネージ コード DCOM を WCF に移行する](../../../docs/framework/interop/how-to-migrate-managed-code-dcom-to-wcf.md)  
 最も安全なソリューションのマネージ DCOM コードを WCF に移行する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [COM のデータ型](https://msdn.microsoft.com/en-us/library/sak564ww(v=vs.100).aspx)  
 対応するマネージとアンマネージのデータ型を提供します。  
  
 [COM 呼び出し可能ラッパーのカスタマイズ](https://msdn.microsoft.com/en-us/library/3bwc828w(v=vs.100).aspx)  
 使用してデータ型を明示的にマーシャ リングする方法について説明します、<xref:System.Runtime.InteropServices.MarshalAsAttribute>デザイン時の属性です。  
  
 [ランタイム呼び出し可能ラッパーのカスタマイズ](https://msdn.microsoft.com/en-us/library/e753eftz(v=vs.100).aspx)  
 相互運用アセンブリで型のマーシャリング動作を調整する方法、および COM 型を手動で定義する方法について説明します。  
  
 [高度な COM 相互運用性](https://msdn.microsoft.com/en-us/library/bd9cdfyx(v=vs.100).aspx)  
 .NET Framework アプリケーションに COM コンポーネントを組み込む方法についての詳細情報へのリンクを示します。  
  
 [アセンブリからタイプ ライブラリへの変換の要約](https://msdn.microsoft.com/en-us/library/xk1120c3(v=vs.100).aspx)  
 アセンブリからタイプ ライブラリにエクスポート変換するプロセスについて説明します。  
  
 [タイプ ライブラリからアセンブリへの変換の要約](https://msdn.microsoft.com/en-us/library/k83zzh38(v=vs.100).aspx)  
 タイプ ライブラリからアセンブリにインポート変換するプロセスについて説明します。  
  
 [ジェネリック型を使用する相互運用](https://msdn.microsoft.com/en-us/library/ms229590(v=vs.100).aspx)  
 COM 相互運用性のジェネリック型を使用するとき、どのアクションがサポートされるかについて説明します。
