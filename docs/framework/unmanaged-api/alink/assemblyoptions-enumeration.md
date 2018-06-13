---
title: AssemblyOptions 列挙体
ms.date: 03/30/2017
api_name:
- AssemblyOptions
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- AssemblyOptions
helpviewer_keywords:
- Alink API, AssemblyOptions enumeration
- AssemblyOptions enumeration
ms.assetid: 84f83921-64cb-49e3-ac8b-22a0b77b18a8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e3926a0d49b2db02cf52a3cc943b05edc4cc36a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406286"
---
# <a name="assemblyoptions-enumeration"></a>AssemblyOptions 列挙体
アセンブリ オプションを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum _AssemblyOptions {  
    optAssemTitle = 0,  
    optAssemDescription,  
    optAssemConfig,  
    optAssemOS,  
    optAssemProcessor,  
    optAssemLocale,  
    optAssemVersion,  
    optAssemCompany,  
    optAssemProduct,  
    optAssemProductVersion,  
    optAssemCopyright,  
    optAssemTrademark,  
    optAssemKeyFile,  
    optAssemKeyName,  
    optAssemAlgID,  
    optAssemFlags,  
    optAssemHalfSign,  
    optAssemFileVersion,  
    optAssemSatelliteVer,  
    optLastAssemOption  
}   AssemblyOptions;  
```  
  
## <a name="fields"></a>フィールド  
  
|フィールド|説明|  
|-----------|-----------------|  
|optAssemTitle|文字列 - アセンブリのタイトルを表します。|  
|optAssemDescription|文字列 - アセンブリの説明が含まれています。|  
|optAssemConfig|文字列 - アセンブリの構成が含まれています。|  
|optAssemOS|エンコードされた - 文字列:"dwOSPlatformId.dwOSMajorVersion.dwOSMinorVersion"です。|  
|optAssemProcessor|ULONG|  
|optAssemLocale|文字列 - アセンブリのロケールが含まれています。|  
|optAssemVersion|エンコードされた - 文字列:"Major.Minor.Build.Revision"です。|  
|optAssemCompany|文字列 - 会社が含まれています。|  
|optAssemProduct|文字列 - 製品名を格納します。|  
|optAssemProductVersion|文字列 (InformationalVersion とも呼ばれます)。|  
|optAssemCopyright|文字列 - 著作権情報が含まれています。|  
|optAssemTrademark|文字列 - 商標情報を格納します。|  
|optAssemKeyFile|String (ファイル名)。|  
|optAssemKeyName|文字列 (キー名)。|  
|optAssemAlgID|ULONG|  
|optAssemFlags|ULONG|  
|optAssemHalfSign|Bool (DelaySign とも呼ばれます)。|  
|optAssemFileVersion|文字列である"Major.Minor.Build.Revision"--ProductVersion と同じようにエンコードします。|  
|optAssemSatelliteVer|文字列である"Major.Minor.Build.Revision"としてエンコードします。|  
|optLastAssemOption|要素の数のカウンターです。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** alink.h  
  
 **ライブラリ**: alink.dll  
  
## <a name="see-also"></a>関連項目  
 [Al.exe (アセンブリ リンカー)](../../../../docs/framework/tools/al-exe-assembly-linker.md)
