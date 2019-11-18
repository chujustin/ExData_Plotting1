download.file("https://d396qusza40orc.cloudfront.net/exdata%2Fdata%2Fhousehold_power_consumption.zip", destfile = "household_power_data.zip")

unzip("household_power_data.zip", exdir = "Household power data")


power <- read.table("Household power data/household_power_consumption.txt", header=T, sep = ";", )


power[, c(3:9)] <- sapply(power[, c(3:9)], as.character)
power[, c(3:9)] <- sapply(power[, c(3:9)], as.numeric)
power[, 1] <- as.Date(power[, 1], format = "%d/%m/%Y")

subpower <- subset(power, Date == "2007-02-01" | Date == "2007-02-02")

subpower$Time <- as.character(subpower$Time)
subpower$Time <- paste(paste(subpower$Date, subpower$Time))
subpower[, 2] <- as.POSIXct(subpower[, 2], format = "%Y-%m-%d %T")

par(mfrow = c(2,2))

#plot (1,1)
with(subpower, plot(Time, Global_active_power,type="l", xlab = "", ylab = "Global Active Power"))

#plot (1,2)
with(subpower, plot(Time, Voltage, type="l", xlab = "datetime", ylab = "Voltage"))

#plot (2,1)
with(subpower, plot(Time, Sub_metering_1, col="black", type = "l", ylab = "Sub metering energy",xlab = ""))
with(subpower, lines(Time, Sub_metering_2, col="red"))
with(subpower, lines(Time, Sub_metering_3, col="blue"))
legend("topright", col = c("black", "red", "blue"), bty = "n", legend = c("Sub_metering_1", "Sub_metering_2","Sub_metering_3"), lwd = 1, lty = 1)

#plot (2,2)
with(subpower, plot(Time, Global_reactive_power, type="l", xlab = "datetime", ylab = "Global_Reactive_Power"))