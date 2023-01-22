
-LAST_VALUE를 사용할 때, 중복된 행을 Return 하는 경우를 막기 위해 DISTINCT 구문 추가

select distinct
    bike_number,
    LAST_VALUE(end_time)
    OVER(
        PARTITION BY bike_number
        ORDER BY end_time ASC
        RANGE BETWEEN 
            UNBOUNDED PRECEDING AND 
            UNBOUNDED FOLLOWING
    ) last_used
from dc_bikeshare_q1_2012
order by last_used desc;
