---
title: .NET Framework アプリケーションにおける COM 相互運用性 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a3e19f8c0a06308a604d2b219f730bf175fb0c46
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>.NET Framework アプリケーションにおける COM 相互運用性 (Visual Basic)
同じアプリケーションの COM オブジェクトと .NET Framework オブジェクトを使用する場合は、オブジェクトがメモリ内に存在する方法の違いに対処する必要があります。 .NET Framework オブジェクトは、マネージ メモリにある: 共通言語ランタイムによって制御されるメモリ:、必要に応じて、ランタイムによって移動することがあります。 COM オブジェクトでは、アンマネージ メモリ内にあるし、別のメモリ位置に移動するものではありません。 Visual Studio と[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]これらの相互作用を制御するためのツールがマネージし、アンマネージ コンポーネントを提供します。 マネージ コードの詳細については、次を参照してください。[共通言語ランタイム](../../../standard/clr.md)です。  
  
 .NET アプリケーションの COM オブジェクトを使用するだけでなくすることも COM 経由のアンマネージ コードからアクセスできるオブジェクトを開発する Visual Basic を使用するには  
  
 このページのリンクは、COM および .NET Framework のオブジェクト間の相互作用の詳細を提供します。  
  
## <a name="related-sections"></a>関連項目  
 [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md)  
 Visual Basic では、COM オブジェクト、ActiveX コントロール、Win32 の Dll、管理対象のオブジェクトや COM オブジェクトの継承などの COM 相互運用性を説明するトピックへのリンクを提供します。  
  
 [COM 相互運用ラッパー エラー](/cpp/misc/com-interop-wrapper-error)  
 プロジェクト システムは、特定のコンポーネントの COM 相互運用ラッパーを作成できない場合の結果とオプションについて説明します。  
  
 [アンマネージ コードとの相互運用](../../../framework/interop/index.md)  
 簡単な説明、マネージとアンマネージ コード間の相互作用の問題の一部と、さらに調査へのリンクを示します。  
  
 [COM ラッパー](../../../framework/interop/com-wrappers.md)  
 マネージ コードから COM メソッドを呼び出すには、ランタイム呼び出し可能ラッパーと .NET オブジェクトのメソッドを呼び出す COM クライアントを許可する COM 呼び出し可能ラッパーについて説明します。  
  
 [高度な COM 相互運用性](../../../framework/interop/index.md)  
 ラッパー、例外、継承、スレッド処理、イベント、変換、またはマーシャ リングに関する COM 相互運用性を説明するトピックへのリンクを提供します。  
  
 [Tlbimp.exe (タイプ ライブラリ インポーター)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 共通言語ランタイム アセンブリで等価な定義に、COM タイプ ライブラリ内の型定義の変換に使用できるツールについて説明します。
