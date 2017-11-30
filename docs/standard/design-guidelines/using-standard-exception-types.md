---
title: "標準例外型の使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 91cd9a03ad1acf61681ecfad0edb061802c4362c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="using-standard-exception-types"></a>標準例外型の使用
このセクションでは、フレームワークとその使用方法の詳細によって提供される標準の例外について説明します。 一覧は完全ではではありません。 その他のフレームワークの例外の種類の使用率の .NET Framework リファレンス ドキュメントを参照してください。  
  
## <a name="exception-and-systemexception"></a>例外と SystemException  
 **X しないで**スロー<xref:System.Exception?displayProperty=nameWithType>または<xref:System.SystemException?displayProperty=nameWithType>です。  
  
 **X しないで**キャッチ`System.Exception`または`System.SystemException`framework コードで再スローする場合を除き、します。  
  
 **避け x**キャッチ`System.Exception`または`System.SystemException`、トップレベルの例外ハンドラーでは可します。  
  
## <a name="applicationexception"></a>ApplicationException  
 **X しないで**スロー サービスまたはそれから派生<xref:System.ApplicationException>です。  
  
## <a name="invalidoperationexception"></a>InvalidOperationException  
 **✓ しないで**スロー、<xref:System.InvalidOperationException>オブジェクトが不適切な状態である場合。  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a>ArgumentException、ArgumentNullException、および ArgumentOutOfRangeException  
 **✓ しないで**スロー<xref:System.ArgumentException>またはメンバーに無効な引数が渡された場合は、そのサブタイプのいずれか。 該当する場合は、最派生例外の種類を選びます。  
  
 **✓ しないで**設定、`ParamName`プロパティのサブクラスのいずれかをスローするときに`ArgumentException`です。  
  
 このプロパティは、例外がスローされる原因となったパラメーターの名前を表します。 コンス トラクター オーバー ロードのいずれかを使用して、プロパティを設定できることに注意してください。  
  
 **✓ は**使用`value`プロパティ set アクセス操作子の暗黙的な値パラメーターの名前。  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a>NullReferenceException、IndexOutOfRangeException、および AccessViolationException  
 **X しないで**明示的または暗黙的にスローする、api で公開されている呼び出し可能<xref:System.NullReferenceException>、 <xref:System.AccessViolationException>、または<xref:System.IndexOutOfRangeException>です。 これらの例外は予約されておりとほとんどの場合は、バグを示す場合に、実行エンジンによってスローされます。  
  
 引数に、これらの例外がスローされないようにチェックを実行します。 時間の経過と共に変わる可能性があるメソッドの実装の詳細を公開するこれらの例外をスローします。  
  
## <a name="stackoverflowexception"></a>StackOverflowException  
 **X しないで**を明示的にスロー<xref:System.StackOverflowException>です。 CLR によってのみ、例外が明示的にスローする必要があります。  
  
 **X しないで**キャッチ`StackOverflowException`です。  
  
 ほとんどでは、一貫性のある任意のスタック オーバーフローが存在する場合に残っているマネージ コードを記述することはできません。 CLR のアンマネージ部分一貫して任意のスタック オーバーフローからバックアップではなくプローブを使用してスタックのオーバーフローを適切に定義された場所に移動するでします。  
  
## <a name="outofmemoryexception"></a>OutOfMemoryException  
 **X しないで**を明示的にスロー<xref:System.OutOfMemoryException>です。 この例外では、CLR インフラストラクチャによってのみスローされます。  
  
## <a name="comexception-sehexception-and-executionengineexception"></a>ComException、SEHException、および ExecutionEngineException  
 **X しないで**を明示的にスロー <xref:System.Runtime.InteropServices.COMException>、 <xref:System.ExecutionEngineException>、および<xref:System.Runtime.InteropServices.SEHException>です。 これらの例外では、CLR インフラストラクチャによってのみスローされます。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [例外のデザイン ガイドライン](../../../docs/standard/design-guidelines/exceptions.md)
