# days to dates
awk -F, -vOFS=, 'NR<2;NR>1{print strftime("%Y,%m,%d",mktime("1950 1 "$1" 0 0 0")),$2,$3}' run301 > run301.dat

# Monthly avg
awk -F, -vOFS=, 'NR<2;NR>1{d=$1","$2;Osum[d]+=$4;Oi[d]++;Msum[d]+=$5;Mi[d]++}END{n=asorti(Mi,R);for(x=1;x<=n;x++)print R[x],Osum[R[x]]/Oi[R[x]],Msum[R[x]]/Mi[R[x]]}' run301.dat > run301.dat.avg



