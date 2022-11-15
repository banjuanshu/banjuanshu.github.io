---
layout: post
title:  "Golang AES Encrypt"
info: "Golang Encrypt"
tech: "Golang"
type: "coding"
---


## Golang AES Encrypt

```golang

package lib

import (
	"crypto/aes"
	"crypto/cipher"
	"encoding/base64"
)

var commonIV = []byte{0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x0a, 0x0b, 0x0c, 0x0d, 0x0e, 0x0f}

func AesEncrypt(plainText string, keyText string) (str string, err error) {
	// 转换成字节数据, 方便加密
	plainByte := []byte(plainText)
	keyByte := []byte(keyText)
	// 创建加密算法aes
	c, err := aes.NewCipher(keyByte)
	if err != nil {
		return "", err
	}
	//加密字符串
	cfb := cipher.NewCFBEncrypter(c, commonIV)
	cipherByte := make([]byte, len(plainByte))
	cfb.XORKeyStream(cipherByte, plainByte)

	str = base64.StdEncoding.EncodeToString(cipherByte)

	return str, err
}

func AesDecrypt(enstr, keyText string) (plainText string, err error) {

	enstr2, _ := base64.StdEncoding.DecodeString(enstr)
	cipherByte := []byte(enstr2)

	// 转换成字节数据, 方便加密
	keyByte := []byte(keyText)

	// 创建加密算法aes
	c, err := aes.NewCipher(keyByte)
	if err != nil {
		return "", err
	}

	// 解密字符串
	cfbdec := cipher.NewCFBDecrypter(c, commonIV)
	plainByte := make([]byte, len(cipherByte))
	cfbdec.XORKeyStream(plainByte, cipherByte)
	plainText = string(plainByte)

	return plainText, err
}

func main() {
	plain := "The text need to be encrypt."
    // AES 规定有3种长度的key: 16, 24, 32分别对应AES-128, AES-192, or AES-256
	key := "abcdefgehjhijkmlkjjwwoew"
	// 加密
	cipherByte, err := AesEncrypt(plain, key)
	if err != nil {
		fmt.Println(err)
	}
	fmt.Printf("%s ==> %x\n", plain, cipherByte)
	// 解密
	plainText, err := AesDecrypt(cipherByte, key)
	if err != nil {
		fmt.Println(err)
	}
	fmt.Printf("%x ==> %s\n", cipherByte, plainText)
}

```
