# PATH TESTING ANALYSIS

## Program Perhitungan Nilai Akhir Mahasiswa UIN Jakarta

## 1. Deskripsi Program

Program menerima nilai Tugas/Formative, UTS, dan UAS kemudian menghitung nilai akhir dengan rumus:

**Nilai Akhir = (20% × Tugas) + (30% × UTS) + (50% × UAS)**

Kategori nilai:

- A: Nilai Akhir ≥ 80
- B: 70 ≤ Nilai Akhir < 80
- C: 60 ≤ Nilai Akhir < 70
- D: 50 ≤ Nilai Akhir < 60
- E: Nilai Akhir < 50

## 2. Algoritma

1. Input nilai Tugas, UTS, dan UAS.
2. Hitung Nilai Akhir.
3. Tentukan grade:
   - Jika nilai ≥ 80 → A
   - Jika nilai ≥ 70 → B
   - Jika nilai ≥ 60 → C
   - Jika nilai ≥ 50 → D
   - Selain itu → E
4. Tampilkan nilai dan grade.

## 3. Control Flow Graph (CFG)

CFG menggambarkan aliran kontrol program berdasarkan statement dan decision.

*Tempatkan gambar CFG di sini.*

## 4. Analisis Node CFG

| Node | Nama Node | Jenis |
|---|---|---|
| 1 | START | Start |
| 2 | Input nilai | Statement |
| 3 | Hitung Nilai Akhir | Statement |
| 4 | Nilai ≥ 80? | Decision |
| 5 | Nilai ≥ 70? | Decision |
| 6 | Nilai ≥ 60? | Decision |
| 7 | Nilai ≥ 50? | Decision |
| 8 | Grade A | Statement |
| 9 | Grade B | Statement |
| 10 | Grade C | Statement |
| 11 | Grade D | Statement |
| 12 | Grade E | Statement |
| 13 | Output | Statement |
| 14 | END | End |

## 5. Analisis Edge

Edge yang terbentuk:

```text
1 → 2 → 3 → 4

4(T) → 8 → 13 → 14
4(F) → 5

5(T) → 9 → 13 → 14
5(F) → 6

6(T) → 10 → 13 → 14
6(F) → 7

7(T) → 11 → 13 → 14
7(F) → 12 → 13 → 14
```

## 6. Cyclomatic Complexity

Jumlah decision node = 4

Rumus:

**V(G) = jumlah decision + 1**

**V(G) = 4 + 1 = 5**

Maka terdapat **5 independent path**.

## 7. Basis Path Testing

### Path 1

```text
1-2-3-4(T)-8-13-14
```

Kondisi: Nilai Akhir ≥ 80

### Path 2

```text
1-2-3-4(F)-5(T)-9-13-14
```

Kondisi: 70 ≤ Nilai Akhir < 80

### Path 3

```text
1-2-3-4(F)-5(F)-6(T)-10-13-14
```

Kondisi: 60 ≤ Nilai Akhir < 70

### Path 4

```text
1-2-3-4(F)-5(F)-6(F)-7(T)-11-13-14
```

Kondisi: 50 ≤ Nilai Akhir < 60

### Path 5

```text
1-2-3-4(F)-5(F)-6(F)-7(F)-12-13-14
```

Kondisi: Nilai Akhir < 50

## 8. Test Case

| TC | Input (Tugas, UTS, UAS) | Nilai Akhir | Path | Output |
|---|---|---:|---|---|
| TC01 | 90, 85, 90 | 88 | Path 1 | A |
| TC02 | 75, 75, 75 | 75 | Path 2 | B |
| TC03 | 65, 65, 65 | 65 | Path 3 | C |
| TC04 | 55, 55, 55 | 55 | Path 4 | D |
| TC05 | 40, 40, 40 | 40 | Path 5 | E |

## 9. Kesimpulan

Program memiliki **4 decision node** sehingga menghasilkan **Cyclomatic Complexity = 5** dan **5 independent path**.

Kelima path telah memiliki test case yang mewakili setiap kemungkinan grade dari A sampai E.
