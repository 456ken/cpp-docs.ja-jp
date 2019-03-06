---
title: /Fi (出力ファイル名のプリプロセス)
ms.date: 11/04/2016
f1_keywords:
- /Fi
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
ms.openlocfilehash: 02d2a27f0a3d6b6aee6c2cd6f7161c9de718446d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414027"
---
# <a name="fi-preprocess-output-file-name"></a>/Fi (出力ファイル名のプリプロセス)

出力ファイルの名前を指定します、 [/P (ファイルへのプリプロセス)](../../build/reference/p-preprocess-to-a-file.md)コンパイラ オプションは、前処理済みの出力を書き込みます。

## <a name="syntax"></a>構文

```
/Fipathname
```

#### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|`pathname`|によって生成された出力ファイルのパスと名前、 **/P**コンパイラ オプション。|

## <a name="remarks"></a>Remarks

使用して、 **/Fi**コンパイラ オプションと組み合わせて、 **/P**コンパイラ オプション。

パスを指定する場合、`pathname`パラメーター、ソース ファイルの基本名、前処理済みの出力ファイルのベース名として使用されます。 `pathname`パラメーターでは、特定のファイル名拡張子は必要ありません。 ただし、".i"の拡張機能は、ファイル名拡張子を指定しない場合に使用されます。

## <a name="example"></a>例

次のコマンド ライン PROGRAM.cpp を前処理し、コメントを保持、追加[#line](../../preprocessor/hash-line-directive-c-cpp.md)ディレクティブ、MYPROCESS.i ファイルに結果を書き出すとします。

```
CL /P /FiMYPROCESS.I PROGRAM.CPP
```

## <a name="see-also"></a>関連項目

[コンパイラ オプション](../../build/reference/compiler-options.md)<br/>
[/P (ファイルの前処理)](../../build/reference/p-preprocess-to-a-file.md)<br/>
[パス名の指定](../../build/reference/specifying-the-pathname.md)
