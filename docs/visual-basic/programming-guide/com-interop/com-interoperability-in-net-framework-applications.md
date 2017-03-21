---
title: ".NET Framework アプリケーション (Visual Basic) での COM 相互運用性 |Microsoft ドキュメント"
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
- interoperability, COM and .NET framework objects
- COM interop
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 308ee8e495efa9368ef55d781f6b6dc314db51ac
ms.lasthandoff: 03/13/2017

---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>.NET Framework アプリケーションにおける COM 相互運用性 (Visual Basic)
同じアプリケーションの COM オブジェクトと .NET Framework のオブジェクトを使用する場合は、オブジェクトをメモリにする方法の違いに対処する必要があります。 .NET Framework オブジェクトがマネージ メモリ内に、共通言語ランタイムによって制御されるメモリ: 必要に応じて、ランタイムによって移動できます。 COM オブジェクトでは、アンマネージ メモリ内にあり、別のメモリ位置に移動するものではありません。 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)]および[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]これらの相互作用を制御するためのツールがマネージし、アンマネージ コンポーネントを提供します。 マネージ コードに関する詳細については、次を参照してください。[共通言語ランタイム](http://msdn.microsoft.com/library/059a624e-f7db-4134-ba9f-08b676050482)します。  
  
 .NET アプリケーションで COM オブジェクトを使用するだけでなくすることも使用する[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]COM 経由のアンマネージ コードからアクセス可能なオブジェクトを開発するには  
  
 このページのリンクは、COM および .NET Framework のオブジェクト間の対話についての詳細を提供します。  
  
## <a name="related-sections"></a>関連項目  
 [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md)  
 COM オブジェクト、ActiveX コントロール、Win32 Dll、マネージ オブジェクトおよび COM オブジェクトの継承を含む Visual Basic での COM 相互運用性を説明するトピックへのリンクを提供します。  
  
 [COM 相互運用ラッパー エラー](https://docs.microsoft.com/cpp/misc/com-interop-wrapper-error)  
 プロジェクト システムは、特定のコンポーネントの COM 相互運用ラッパーを作成できない場合の結果とオプションについて説明します。  
  
 [アンマネージ コードとの相互運用](https://msdn.microsoft.com/library/sd10k43k)  
 について簡単にマネージ コードとアンマネージ コード間の相互作用の問題のいくつかについて説明し、詳細な情報へのリンクを示します。  
  
 [COM ラッパー](http://msdn.microsoft.com/library/e56c485b-6b67-4345-8e66-fd21835a6092)  
 マネージ コードを COM メソッドを呼び出すには、ランタイム呼び出し可能ラッパーと、.NET オブジェクトのメソッドを呼び出す COM クライアントを許可する COM 呼び出し可能ラッパーについて説明します。  
  
 [高度な COM 相互運用性](http://msdn.microsoft.com/en-us/3ada36e5-2390-4d70-b490-6ad8de92f2fb)  
 ラッパー、例外、継承、スレッド処理、イベント、変換、またはマーシャ リングに関する COM 相互運用性を説明するトピックへのリンクを提供します。  
  
 [Tlbimp.exe (タイプ ライブラリ インポーター)](http://msdn.microsoft.com/library/ec0a8d63-11b3-4acd-b398-da1e37e97382)  
 共通言語ランタイム アセンブリで等価な定義に、COM タイプ ライブラリ内で見つかった種類の定義の変換に使用できるツールについて説明します。
