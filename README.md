# registerchemacquire
% read images, these images are already greyscale images
A = imread('fix.TIF');
B = imread('move.TIF');

%if fixed is brighter than moving, then it is magneta, otherwise, it is green
% figure, imshowpair(A,B)
% title('Unregistered')

%do(A-B)and show the image, adjust the intensity of E to show it 
% E=minus(A,B);
% F=imadjust(E);
% figure, imshow(F);

% translate image A (move A) to register it with B, []
a=10;
b=10;
c=512-2*a;
d=512-2*b;
J=imtranslate(A,[a,b],'OutputView','full');
%figure, imshowpair(J,B);
%title('translate')

% BW2=edge(B,'Canny');
% crop image A and B to make them same size
I1 = imcrop(J,[a b c d]);
I2 = imcrop(B,[a b c d]);

%figure, imshowpair(I1,I2);

C=minus(I1,I2);


D=imadjust(C);


imshow(D);

% save image as "result.tif" and open it in ChemImage to analyze it

%find the intensity of ROI
% improfile




