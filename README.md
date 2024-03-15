#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_LENGTH 2024
#define MIN_LENGTH 1945

void lessThanRequired(int *lengthOfText){
    printf("The length of your text is less than specified, please update your text\n");
    printf("Length Before : %d\n", *lengthOfText);
    *lengthOfText = MIN_LENGTH;
}

void equalThanRequired(int *lengthOfText){
    printf("Thank you, Your text length is correct\n");
}

void moreThanRequired(int *lengthOfText){
    printf("Your text is too long, please reduce the text\n");
    printf("Length Before : %d\n", *lengthOfText);
    *lengthOfText = MIN_LENGTH;
}

int checkLenghtRequirement(char* text){
    int length = strlen(text);
    if (length < MIN_LENGTH)
        return 0;
    else if (length == MIN_LENGTH)
        return 1;
    else
        return 2;
}

int main() {
    int lengthOfText, selectOption;
    FILE *fptr = NULL;
    char text[MAX_LENGTH];

    fptr = fopen("C:/Users/pc/Desktop/file.txt", "r");

    if(fptr == NULL){
        printf("Error: Unable to open the file\n");
        exit(1);
    }

    if (fgets(text, MAX_LENGTH, fptr) == NULL) {
        printf("Error: Unable to read text from the file\n");
        exit(1);
    }

    fclose(fptr);

    lengthOfText = strlen(text);

    selectOption = checkLenghtRequirement(text);

    void (*functions[3])(int*) = {lessThanRequired, equalThanRequired, moreThanRequired};

    functions[selectOption](&lengthOfText);
     // TODO
    // Pada fungsi checkLenghtRequirement akan mengembalikan sebuah angka
    // angka tersebut digunakan untuk memilih secara otomatis salah satu fungsi yang digunakan
    // jika fungsi checkLenghtRequirement() mengembalikan nilai 0, maka
    //      panggil fungsi lessThanRequired,
    //      tampilkan - > The length of your text is less than specified, please update your text, dan
    //      update nilai lengthOfText ke minimum requirement melalui pointer menggunakan operasi aritmatika

    // jika fungsi checkLenghtRequirement() mengembalikan nilai 1, maka
    //      panggil fungsi equalThanRequired, dan
    //      tampilkan - > Thank you, Your text length is correct

    // jika fungsi checkLenghtRequirement() mengembalikan nilai 2, maka
    //      panggil fungsi moreThanRequired
    //      tampilkan - > Your text is to long, please reduce the text
    //      update nilai lengthOfText ke maximum requirement melalui pointer menggunakan operasi aritmatika

    // setiap fungsi harus memiliki minimal 1 parameter yang merefrensikan variabel panjang dari text
    
    // Catatan :
    //      - tidak diperkenankan menggunakan if atau switch, baik dalam main() atau fungsi yang telah tersedia
    //        untuk mengkondisikan output dari fungsi checkLenghtRequirement dan memanggil fungsi yang
    //        telah ditentukan
    //      - baris kode tidak lebih dari 100 (include comment ini)
    //      - tidak diperkenankan mengganti yang tertera pada starter code dalam alasan apapun

    // Input :
    // Isi File -> Tempor sunt quis magna reprehenderit irure irure mollit ex reprehenderit incididunt ex enim. Do eu cillum fugiat sunt reprehenderit. Aute in consequat nulla irure pariatur occaecat velit. Occaecat anim Lorem nulla exercitation dolore et. Qui ea Lorem in consequat nisi exercitation id ad aliqua Lorem anim eu ad.

    // Output :
    // The length of your text is less than specified, please update your text
    // Length Before : 312
    // The Lenght is updated to 2023

    printf("\nThe Lenght is updated to %d", lengthOfText);

    return 0;
}
